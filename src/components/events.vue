<template>
	<div id="events">
		<div class="alert alert-danger" role="alert" v-for="event in events.events" v-if="events.events.length">
			{{events.lastEvent}}
		</div>
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
		padding: 5px 15px;
	}
</style>
