<template>
    <div>
        <h2>Zajęcia</h2>
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <meetings-list :meetings="meetings" :username="username" :participants="participants"
                       @added="addNewParticipant($event)"></meetings-list>
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
            };
        },
        methods: {
            addNewMeeting(meeting) {
                meeting.participants=[];
                this.meetings.push(meeting);
            },
            addNewParticipant(username) {
                this.participants.push(username);
            },

            deleteParticipant(username) {
                this.participants.delete(username);
            }

        }
    }
</script>