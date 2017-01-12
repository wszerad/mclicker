<template>
	<div class="upgrade" @click="activate()" :class="{'active': item.active, 'available': !item.active && available}">
		<div v-if="item.active">
			<header>
				{{item.title}}
			</header>
			<article>
				{{item.text}}
			</article>
		</div>
		<div v-else>
			{{item.cost}}
		</div>
	</div>
</template>

<script type="text/babel">
	import engine from '../services/engine.vue';

	export default {
		name: 'upgrade',
		props: ['item'],
		computed: {
			available() {
				return this.item.realCost <= engine.founds;
			}
		},
		data() {
			return {};
		},
		methods: {
			activate() {
				engine.activate(this.item);
			}
		}
	}
</script>

<style lang="sass" rel="stylesheet/scss">
	.upgrade {
		background: #ff4222;
		margin-bottom: 5px;
		padding: 10px;
		border-radius: 2px;
		font-weight: bold;

		article {
			font-weight: 300;
		}

		&.active {
			background-color: #4490b8;
		}

		&.available {
			background-color: #5cb85c;
		}
	}
</style>
