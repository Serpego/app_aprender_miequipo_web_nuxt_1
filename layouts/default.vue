<template>
	<div id="app">
		<b-navbar toggleable="sm" type="dark" variant="info">
			<b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
			<b-navbar-brand to="/">MiEquipo</b-navbar-brand>
			<b-collapse is-nav id="nav_collapse">
				<b-navbar-nav v-if="$auth.loggedIn">
					<b-nav-item to="/proyectos">Proyectos</b-nav-item>
					<b-nav-item to="/oficios">Oficios</b-nav-item>
				</b-navbar-nav>

				<!-- Right aligned nav items -->
				<b-navbar-nav class="ml-auto">
					<b-nav-item-dropdown v-if="$auth.loggedIn" right>
						<template slot="button-content">
							<em>Mi Usuario</em>
						</template>
						<b-dropdown-item to="mi-perfil">Perfil</b-dropdown-item>
						<b-dropdown-item @click="$auth.logout()">Salir</b-dropdown-item>
					</b-nav-item-dropdown>
				</b-navbar-nav>
			</b-collapse>
		</b-navbar>

    <nuxt/>

 	  <footer class="footer">
      <div class="container">
       	<b-link href="https://podemosaprender.org">&copy; Podemos Aprender</b-link> |
       	<b-link to="/privacidad">Políticas de Privacidad</b-link> |
       	<b-link to="/privacy">Privacy policy</b-link> |
       	<b-link to="/tos">Terms of service</b-link> |
      </div>
    </footer>
  </div>
</template>

<style>
html {
  position: relative;
  min-height: 100%;
}
body {
  /* Margin bottom by footer height */
  margin-bottom: 60px;
}
.footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  /* Set the fixed height of the footer here */
  height: 60px;
  line-height: 60px; /* Vertically center the text there */
  background-color: #e0e0e0;
	font-size: 0.8em;
}
</style>
