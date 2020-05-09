<template>
    <div>

        <div v-show="authenticatedUsername">
            <h1>System zapisów na zajęcia</h1>
            <user-panel :username="authenticatedUsername" @logout="logMeOut($event)"></user-panel>
            <meeting-page :username="authenticatedUsername"></meeting-page>
        </div>

        <div v-if="authenticatedUsername===''">
            <h1>Witaj w systemie zapisów na zajęcia</h1>
            <login-form @login="logMeIn($event)"></login-form>
        </div>

    </div>

</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import UserPanel from "./UserPanel";
    import MeetingPage from "./meetings/MeetingPage";

    export default {
        components: {LoginForm, UserPanel, MeetingPage},
        data() {
            return {
                authenticatedUsername: ''
            };
        },
        methods: {
            logMeIn(username) {
                this.authenticatedUsername = username;
            },
            logMeOut() {
                this.authenticatedUsername = '';
            }
        }
    }
</script>

<style>

</style>
