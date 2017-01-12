<template>
	<div id="events">
		<transition-group name="event">
			<div class="alert alert-danger" role="alert" v-for="event in events.events" :key="event.id">
				{{event.msg}}
			</div>
		</transition-group>
	</div>
</template>

<script type="text/babel">
	import events from '../services/events.vue';

	export default {
		name: 'events',
		data() {
			return {
				events
			};
		}
	}
</script>

<style lang="sass" rel="stylesheet/scss">
	#events {
		position: relative;
		z-index: 9999;

		.alert {
			position: absolute;
			width: 100%;
			top: 0;
			left: 0;
			margin: 10px;
			opacity: 1;
		}

		.event-enter-active, .event-leave-active {
			transition: all .5s ease;
		}

		.event-enter {
			transform: translateY(-50px);
			opacity: 0;
		}

		.event-leave-to {
			transform: translateY(-50px);
			opacity: 0;
		}
	}
</style>
