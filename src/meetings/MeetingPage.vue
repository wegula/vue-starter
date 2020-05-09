<template>
    <div>
        <h2>Zajęcia</h2>
        <button @click="meetingForm=true" v-if="!meetingForm">Dodaj nowe spotkanie</button>
        <new-meeting-form @added="addNewMeeting($event)" v-if="meetingForm"></new-meeting-form>
        <meetings-list :meetings="meetings" :username="username"
                       @addparticipant="addNewParticipant($event)"
                       @deleteparticipant="deleteParticipant($event)"
                       @deletemeeting="deleteMeeting($event)"
        ></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        props: ['username'],
        components: {NewMeetingForm, MeetingsList},
        data() {
            return {
                meetings: [],
                meetingForm: false,
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
                this.meetingForm = false;
            },
            addNewParticipant(meetingName) {
                let meeting;
                for (let i = 0; i < this.meetings.length; i++) {
                    meeting = this.meetings[i];
                    if (meeting.name === meetingName) {
                        meeting.participants.push(this.username);
                    }
                }
            },

            deleteParticipant(meetingName) {
                let meeting;
                for (let i = 0; i < this.meetings.length; i++) {
                    meeting = this.meetings[i];
                    if (meeting.name === meetingName) {
                        meeting.participants.splice(meeting.participants.indexOf(this.username));
                    }
                }
            },
            deleteMeeting(meetingName) {
                for (let i = 0; i < this.meetings.length; i++) {
                    if (this.meetings[i].name === meetingName){
                        this.meetings.splice(i);
                    }
                }
            }
        }
    }

</script>