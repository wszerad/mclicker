<script type="text/babel">
	import Vue from 'vue';

	const engine = new Vue({
		data(){
			return {
				clients: 0,
				performance: 0,
				level: 0,
				progress: 0,
				founds: 100,
				click: 0,
				income: 0
			}
		},
		methods: {
			activate(item) {
				if(item.realCost <= this.founds) {
					this.founds -= item.realCost;
					item.active = true;
				}
			}
		}
	});

	export default engine;
</script>