<template>
<table>
<!--  v-if="meetings.length > 0" -->
	<thead>
		<tr>
			<th>Nazwa spotkania</th>
			<th>Opis</th>
			<th>Uczestnicy</th>
			<th></th>
			<th></th>
		</tr>
	</thead>
	<tbody>
		<tr v-for="meeting in meetings" :key="meeting.name">
			<td>{{ meeting.name }}</td>
			<td>{{ meeting.description }}</td>

			<td>
				<ul>
					<li v-for="participant in meeting.participants" :key="participant">{{participant}}</li>
				</ul>
			</td>

			<td></td>

			<td v-if="meeting.participants.length === 0">
				<button @click=remove(meeting) style="float: right; margin-left: 5px">Usuń puste spotkanie</button>
				<button @click=signup(meeting) class="button button-outline" style="float: right">Zapisz się</button>
			</td>

			<td
				v-else-if="!meeting.participants.find(item => item === username)">
				<button @click=signup(meeting) class="button button-outline" style="float: right">Zapisz się</button>
			</td>

			<td v-else>
				<button @click=signout(meeting) class="button button-outline"
					style="float: right">Wypisz się</button>
			</td>
		</tr>
	</tbody>
</table>
</template>

<script>
export default {
    props: ['meetings','username'],
    methods: {
	signup(meeting) {
            this.$emit('signup', meeting);
        },
    signout(meeting) {
            this.$emit('signout', meeting);
        },
    remove(meeting) {
            this.$emit('removed', meeting);
        }
    
    }
}
</script>