<template>
<table v-if="meetings.length > 0">
	<thead>
		<tr>
			<th>Nazwa spotkania</th>
			<th>Opis</th>
			<th>Uczestnicy</th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr v-for="meeting in meetings" :key="meeting.name">
			<td>{{ meeting.name }}</td>
			<td>{{ meeting.description }}</td>
			<td>
				<ul>
					<li v-for="participant in meeting.participants" :key="participant">
						{{participant}}</li>
				</ul>
			</td>
			<td v-if = "!meeting.participants.find((element)=> element == username)">
				<button>Wypisz się</button>
			</td>
			<td v-else>
				<button>Zapisz się</button>
			</td>
		</tr>
	</tbody>
</table>
</template>

<script>
export default {
    props: ['meetings','username']
}
</script>