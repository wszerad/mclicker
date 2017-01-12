<script type="text/babel">
	import Vue from 'vue';

	export default new Vue({
		data() {
			return {
				events: []
			};
		},
		computed: {
			lastEvent() {
				return this.events[this.events.length-1];
			}
		},
		methods: {
			emit(msg) {
				this.events.push(msg);
			}
		}
	});
</script>