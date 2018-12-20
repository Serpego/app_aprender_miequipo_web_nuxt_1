# PodemosAprender App

> MiEquipo en PodemosAprender

#programar #javascript #web #movil  ¿Nos hacemos una app para nosotros? ¿Querés aprender para hacer otras?

La empece a armar en https://miequipo.podemosaprender.org/

(si te chilla por los certificados, aceptalos provisoriamente en las opciones avanzadas)

Por ahora tiene 

* login con google, facebook y registrarse usando un form con captcha

* se trae los proyectos y oficios de la api de blogger, filtrando por un tag (o sea, los cargue en blogger, podria traer de mas lugares como github, otros blogs, etc.)

Si queres espiar el codigo (la joda esta casi toda en pages/ salvo la barra de navegacion que esta en layouts/default.vue )

https://github.com/podemosaprender/app_aprender_miequipo_web_nuxt_1

Tambien estuve preparando el backend, que autentica de verdad y guarda tu perfil, que proyectos y oficios te interesan, etc.

Asi sabemos que avisarle a quien, que era el objetivo.

Tambien podemos implementar el sistema de puntos que propuso Guillermo Molteni, y páginas interactivas para aprender como las que nos trae  Zanandrea Daniel pero que no nos cobren ;)

Falta incorporar tambien las ideas del form buenisimo que compartio Darijo Bakota que me sirven de ayudamemoria.

¿Qué más pondrias? Estoy tratando de organizar el codigo para que podamos modificarlo entre todos. ¿Qué dicen Sergio Rinal y Ariel Alejandro Ruiz?

## Build Setup

``` bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, checkout [Nuxt.js docs](https://nuxtjs.org).
