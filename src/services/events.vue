<script type="text/babel">
	import Vue from 'vue';

	export default new Vue({
		data() {
			return {
				index: 0,
				events: []
			};
		},
		created() {
			let self = this;
			setInterval(function() {
				if(self.events.length) {
					self.events.splice(0, 1);
				}
			}, 10000);
		},
		methods: {
			emit(msg) {
				this.events.push({
					id: this.index++,
					msg
				});

				if(this.events.length > 2) {
					this.events.splice(0, 1);
				}
			}
		}
	});
</script>