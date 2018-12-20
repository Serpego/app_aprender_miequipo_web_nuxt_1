<template>
		<b-container>
			<h2>Oficios</h2>
          <b-table id="my-table" :fields="fields" :items="itemsTraidosDeBlogger" :busy.sync="isBusy" no-provider-sorting no-provider-filtering no-provider-paging>
            <template slot="img" slot-scope="data">
                <img :src="data.value" style="width: 60px; height: 60px;">
            </template>

            <template slot="link" slot-scope="data">
                <a :href="data.value">
                    {{data.value}}
                </a>
            </template>
          </b-table>
      </b-container>
</template>

    <script>
/* VER: API de blogger, FROM: https://feed.mikle.com/support/google-blogger-rss/
Full site feed:
Atom 1.0: https://blogname.blogspot.com/feeds/posts/default
Comments-only feed:
Atom 1.0: https://blogname.blogspot.com/feeds/comments/default
Label-specific site feed:
To get a feed for a specific label, change [label].
Atom 1.0: https://blogname.blogspot.com/feeds/posts/default/-/[label]
Individual post comment feed:
Note: You can find the postId of an individual post from the Posting > ‘Edit Posts’ tab. Simply mouseover the ‘Edit’ link next to a particular post, and that postId will be displayed in your browser’s status bar.
Atom 1.0: https://blogname.blogspot.com/feeds/postId/comments/default
*/
function entry_kv_blogger(e0) { //U: una entrada del feed de blogger a un kv simple y que se ve en b-table
    //DBG console.log("E0",e0);
    let img= e0.content.$t.match("<img .*?src=\"([^\"]*)"); 
    let e1= { 
        titulo: e0.title.$t,
        tags: e0.category ? e0.category.map(e => e.term).join(", ") : "",
        updated: e0.updated.$t,
        link: e0.link.find(e => e.rel=="alternate").href,
        id: e0.id.$t,
        content: e0.content, //U: el contenido del post, en html
        img: ((img && img[1]) || "/logo512.png"), //U: la url de la primera imagen
    }
    //DBG console.log("E1",e1);
    return e1;
}
                               
//FROM: axios + tabla bootstrap, https://bootstrap-vue.js.org/docs/components/table/
export default {
    data: function () {
      return {
        isBusy: false,
        fields: [
            { key: 'img'},
            { key: 'titulo', sortable: true },
            { key: 'tags', sortable: false },
            { key: 'updated', sortable: true },
            { key: 'link', sortable: false },
        ],
      }
    },
    methods: {
      itemsTraidosDeBlogger (ctx) { //U: trae los items de blogger y los formatea para b-table
        let promise = this.$axios.get('https://cors-anywhere.herokuapp.com/https://pizarra.podemosaprender.org/feeds/posts/default/-/Oficio/?alt=json') //A: de blogger como json
        return promise.then((data) => {
          //DBG: 
          window.XDATA= data; // return([]); //U: Asi hice disponible el resultado en la consola para debuggear
          let a_kv_para_tabla= data.data.feed.entry.map(entry_kv_blogger);
          return(a_kv_para_tabla);
        }).catch(error => {
          return []
        })
      }
    }
}
</script>

