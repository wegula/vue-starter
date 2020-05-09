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
                this.meetings.push(meeting);
            },
            addNewParticipant(meetingName) {
                let meeting;
                for (let i = 0; i < this.meetings.length; i++) {
                    meeting = this.meetings[i];
                    if (meeting.name === meetingName) {
                        meeting.participants.push(this.username);
                    }
                };
            },

            deleteParticipant(meetingName) {
                for (let i = 0; i < this.meetings.length; i++) {
                    if (this.meetings[i].name === meetingName) {
                        this.meetings.splice(i, 1);
                    }
                }
            }

        }
    }
</script>