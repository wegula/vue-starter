<template>
    <div>

        <div v-if="authenticatedUsername">
            <h1>System zapisów na zajęcia</h1>
            <h3>Witaj {{authenticatedUsername}}!
                <button @click="logMeOut()">Wyloguj</button>
            </h3>

        </div>

        <div v-else>
            <h1>Witaj w systemie zapisów na zajęcia</h1>
            <login-form @login="logMeIn($event)"></login-form>
        </div>

    </div>

</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";

    export default {
        components: {LoginForm},
        data() {
            return {
                email: '',
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
