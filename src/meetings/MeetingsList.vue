<template>
    <div v-if="meetings.length > 0">
        <table>
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
                    <button @click="deleteParticipant(meeting.name)" v-if="isParticipantAdded(meeting.participants)">
                        Wypisz się
                    </button>
                    <button @click="addNewParticipant(meeting.name)" v-if="!isParticipantAdded(meeting.participants)">
                        Zapisz się
                    </button>
                    <button @click="deleteMeeting(meeting.name)" v-if="meeting.participants.length===0">
                        Usuń puste spotkanie
                    </button>
                </td>
            </tr>
            </tbody>
        </table>
    </div>
    <div v-else>
        <h3>Brak zaplanowanych spotkań</h3>
    </div>
</template>

<script>
    export default {
        props: ['meetings', 'username'],
        methods: {
            addNewParticipant(meetingName) {
                this.$emit('addparticipant', meetingName);
            },
            deleteParticipant(meetingName) {
                this.$emit('deleteparticipant', meetingName);
            },
            deleteMeeting(meetingName){
                this.$emit('deletemeeting', meetingName)
            },
            isParticipantAdded(participants) {
                if (participants == null || participants.length === 0) return false;
                return participants.includes(this.username);
            }
        }
    }
</script>>

<style scoped>
</style>