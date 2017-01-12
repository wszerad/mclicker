<script type="text/babel">
	import Vue from 'vue';
	import events from '../services/events.vue';

	const engine = new Vue({
		data(){
			return {
				clients: 0,
				performance: 0,
				level: 0,
				lines: 0,
				multiplier: 1,
				founds: 100,
				clicked: 0,
				devs: [],
				boosts: [],
				upgrades: []
			}
		},
		watch: {
			lines(val) {
				if(this.lines > this.neededForLevel) {
					this.lines = this.lines - this.neededForLevel;
					this.level++;
				}
			}
		},
		computed: {
			neededForLevel() {
				return (Math.pow((this.level + 1), 2) + Math.pow((this.level), 2)) * 100;
			},
			progress() {
				return this.lines / this.neededForLevel * 100;
			},
			click() {
				return this.boosts.reduce(function (click, item) {
					click += item.item.performance;
					return click;
				}, 1) * this.multiplier;
			},
			income() {
				return this.clients * Math.pow(this.level, 0.5) * 10;
			}
		},
		methods: {
			activate(item) {
				if(!item.active && item.realCost <= this.founds) {
					this.founds -= item.realCost;
					item.active = true;

					if(item.type === 'dev') {
						this.devs.push(item);
					} else if(item.type === 'boost') {
						this.boosts.push({
							maxTime: item.time,
							time: item.time,
							item
						});
					} else {
						this.upgrades.push(item);
					}

					if(item.event) {
						let event = item.event();
						if(event) {
							events.emit(event);
						}
					}
				}
			},
			recalculate() {
				let perf = this.devs.reduce(function (perf, item) {
					console.log(item.performance);
					perf += item.performance;
					return perf;
				}, 0);

				let i = 0;

				while (i < this.boosts.length) {
					let item = this.boosts[i];

					if (item.time) {
						item.time -= 1;
						i++;
					} else {
						item.item.active = false;
						this.boosts.splice(i, 1);
					}
				}

				let multiplier = 1;
				this.upgrades.forEach(function (item) {
					multiplier *= item.performance / 100;
				});

				this.multipler = multiplier;
				this.performance = perf * multiplier + this.clicked;
				this.clients += this.level;
				this.founds += this.income;
				this.lines += this.performance;
				this.clicked = 0;
			},
			code() {
				this.lines += this.click;
				this.clicked += this.click;
			}
		}
	});

	setInterval(engine.recalculate, 1000);

	export default engine;
</script>