<script>
	import { onMount } from 'svelte';
	import FullCalendar from 'svelte-fullcalendar';

	let options = { initialView: 'dayGridMonth', plugins: [] };

	onMount(async () => {
		options.plugins = [
			(await import('@fullcalendar/daygrid')).default,
		];
	});
</script>

<FullCalendar {options} />