<template>
	<div id="stats">
		<div class="stats-col">
			<form class="form-horizontal">
				<div class="form-group">
					<label class="col-sm-4 control-label">Klienci</label>
					<div class="col-sm-8">
						<input type="text" class="form-control" disabled v-model="engine.clients">
					</div>
				</div>
				<div class="form-group">
					<label class="col-sm-4 control-label">Linii kodu / miesiąc</label>
					<div class="col-sm-8">
						<input type="text" class="form-control" disabled v-model="engine.performance">
					</div>
				</div>
				<div class="form-group">
					<label class="col-sm-4 control-label">Etap</label>
					<div class="col-sm-2">
						<input type="text" class="form-control" disabled v-model="engine.level">
					</div>
					<div class="col-sm-6">
						<div class="progress">
							<div class="progress-bar progress-bar-success progress-bar-striped" role="progressbar" :style="{'width': engine.progress + '%'}"></div>
						</div>
					</div>
				</div>
				<div class="form-group">
					<label class="col-sm-4 control-label">Fundusze</label>
					<div class="col-sm-4">
						<input type="text" class="form-control" disabled v-model="engine.founds">
					</div>
					<div class="col-sm-4">
						<input type="text" class="form-control" disabled v-model="engine.income">
					</div>
				</div>
			</form>
		</div>
		<div class="stats-col">
			<v-clicker></v-clicker>
		</div>
		<div class="stats-col">
			<form class="form-horizontal">
				<div class="form-group">
					<label class="col-sm-4 control-label">Koszty</label>
					<div class="col-sm-8">
						<div class="progress">
							<div class="progress-bar progress-bar-success progress-bar-striped" role="progressbar" style="width: 40%"></div>
						</div>
					</div>
				</div>
			</form>
		</div>
	</div>
</template>

<script type="text/babel">
	import vClicker from './clicker.vue';
	import engine from '../services/engine.vue';

	export default {
		name: 'stats',
		data() {
			return {
				engine
			};
		},
		components: {
			vClicker
		}
	}
</script>

<style lang="sass" rel="stylesheet/scss">
	#stats {
		display: flex;

		.stats-col {
			width: 33%;
		}

		.progress {
			margin-bottom: 0;
			height: 34px;
		}
	}
</style>
