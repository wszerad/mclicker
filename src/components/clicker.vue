<template>
	<div id="clicker">
		<button type="button" class="btn btn-success" @click="code()" :disabled="!engine.clickable">
			<p>
				Programuj
			</p>
			<p>
				+ {{engine.click.toFixed(0)}} / click
			</p>
		</button>
	</div>
</template>

<script type="text/babel">
	import engine from '../services/engine.vue';

	export default {
		name: 'clicker',
		data() {
			return {
				engine
			};
		},
		methods: {
			code() {
				engine.code();
			}
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
