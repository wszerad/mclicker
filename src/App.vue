<template>
	<div id="app">
		<header class="app-header">Zaklepane.com</header>
		<v-stats></v-stats>
		<v-upgrades></v-upgrades>
	</div>
</template>

<script type="text/babel">
	import vStats from './components/stats.vue';
	import vUpgrades from './components/upgrades.vue';

	export default {
		name: 'app',
		data() {
			return {};
		},
		components: {
			vStats,
			vUpgrades
		}
	}
</script>

<style lang="sass" rel="stylesheet/scss">
	@import "./src/vendors/bootstrap/css/bootstrap.css";
	@import "./src/vendors/bootstrap/css/bootstrap-theme.css";

	html, body, #app {
		height: 100%;
	}

	body {
		background-image: url('./src/assets/images/background.jpg');
		background-repeat: repeat;
	}

	#app {
		background-color: rgba(255,255,255,0.8);

		.app-header {
			font-size: 4rem;
		}
	}
</style>
