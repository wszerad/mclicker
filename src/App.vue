<template>
	<div id="app">
		<v-events></v-events>
		<header class="app-header">Zaklepane true story</header>
		<v-stats></v-stats>
		<v-upgrades></v-upgrades>
	</div>
</template>

<script type="text/babel">
	import vStats from './components/stats.vue';
	import vUpgrades from './components/upgrades.vue';
	import vEvents from './components/events.vue';

	export default {
		name: 'app',
		data() {
			return {};
		},
		components: {
			vStats,
			vUpgrades,
			vEvents
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
		position: relative;
		background-color: rgba(255,255,255,0.8);
		overflow-y: scroll;

		.app-header {
			font-size: 6rem;
			font-weight: bold;
			text-align: center;
		}
	}
</style>
