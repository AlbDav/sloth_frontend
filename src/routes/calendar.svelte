<script context="module">
	export const ssr = false;
</script>

<script>
	import { onMount } from 'svelte';
	import { Calendar } from '@fullcalendar/core';
	import dayGridPlugin from '@fullcalendar/daygrid';
	import timeGridPlugin from '@fullcalendar/timegrid';
	import listPlugin from '@fullcalendar/list';
	import { addHours } from 'date-fns';

	let calendarEl;
	let calendar;

	onMount(async () => {
		await import('@fullcalendar/core/vdom');
		calendar = new Calendar(calendarEl, {
			plugins: [dayGridPlugin, timeGridPlugin, listPlugin],
			initialView: 'dayGridMonth',
			headerToolbar: {
				left: 'prev,next today',
				center: 'title',
				right: 'dayGridMonth,timeGridWeek,timeGridDay,listWeek'
			},
			nowIndicator: true,
			events: [
				{
					id: 'e1',
					title: 'Prova',
					start: Date.now(),
					end: addHours(Date.now(), 1),
					backgroundColor: 'red'
				},
				{
					id: 'e2',
					title: 'Prova 2',
					start: addHours(Date.now(), -3),
					end: addHours(Date.now(), -2),
					backgroundColor: 'green'
				},
				{
					id: 'e3',
					title: 'Prova 3',
					start: addHours(Date.now(), 2),
					end: addHours(Date.now(), 3)
				}
			]
		});
		calendar.render();
	});
</script>

<div bind:this={calendarEl} />
