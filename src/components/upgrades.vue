<template>
	<div id="upgrades">
		<div class="col-sm-4">
			<div class="panel panel-info">
					<div class="panel-heading">
					Dopalacze
				</div>
				<div class="panel-body">
					<v-upgrade v-for="item in boosts" :item="item"></v-upgrade>
				</div>
			</div>
		</div>
		<div class="col-sm-4">
			<div class="panel panel-info">
				<div class="panel-heading">
					Klepacze kodu
				</div>
				<div class="panel-body">
					<v-upgrade v-for="item in devs" :item="item"></v-upgrade>
				</div>
			</div>
		</div>
		<div class="col-sm-4">
			<div class="panel panel-info">
				<div class="panel-heading">
					Inwestycje
				</div>
				<div class="panel-body">
					<v-upgrade v-for="item in upgrades" :item="item"></v-upgrade>
				</div>
			</div>
		</div>
	</div>
</template>

<script type="text/babel">
	import vUpgrade from './upgrade.vue';
	import { devs, boosts, upgrades} from './data.vue';

	export default {
		name: 'upgrades',
		data() {
			return {
				devs,
				boosts,
				upgrades
			};
		},
		components: {
			vUpgrade
		}
	}
</script>

<style lang="sass" rel="stylesheet/scss">
	#upgrades {

	}
</style>
