<template>
	<div class="upgrade" @click="activate()" v-show="visible" :class="{'active': item.active, 'available': !item.active && available, 'disabled': item.disabled}">
		<div v-if="item.active">
			<header>
				{{item.title}}
			</header>
			<article>
				{{item.text}}
			</article>
		</div>
		<div v-else>
			<header>
				Koszt:
			</header>
			<article>
				{{item.cost}}
			</article>
		</div>
	</div>
</template>

<script type="text/babel">
	import engine from '../services/engine.vue';

	export default {
		name: 'upgrade',
		props: ['item'],
		computed: {
			visible() {
				let self = this.item;

				function finder(item) {
					return self.dependencies.some(function (name) {
						return item.title === name;
					});
				}

				if(self.dependencies.length) {
					return engine.devs.find(finder) || engine.upgrades.find(finder);
				} else {
					return true;
				}
			},
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

		&.disabled {
			background-color: #ffe60d!important;
		}
	}
</style>
