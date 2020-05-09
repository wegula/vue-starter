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
                <ol>
                    <li v-for="participant in meeting.participants">{{participant}}</li>
                </ol>
            </td>
            <td>
                <div v-if="meeting.participants.length > 0">
                    <button @click="deleteParticipant(meeting.name)">Wypisz się</button>
                </div>
                <div v-else>
                    <button @click="addNewParticipant(meeting.name)">Zapisz się</button>
                </div>
            </td>

        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'username'],
        methods: {
            addNewParticipant(meetingName) {
                this.$emit('addparticipant', this.username, meetingName);
            },
            deleteParticipant(meetingName) {
                this.$emit('deleteparticipant', this.username, meetingName);
            }
        }
    }
</script>>

<style scoped>
</style>