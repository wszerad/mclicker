<template>
	<div id="clicker">
		<button type="button" class="btn btn-success">
			<p>
				Programuj
			</p>
			<p>
				+ {{click}} / click
			</p>
		</button>
	</div>
</template>

<script type="text/babel">
	import { click } from '../services/engine.vue';

	export default {
		name: 'clicker',
		data() {
			return {
				click
			};
		},
		components: {

		}
	}
</script>

<style lang="sass" rel="stylesheet/scss">
	#clicker {
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;

		button {
			text-transform: uppercase;
			height: 100px;
			width: 200px;
		}
	}
</style>
