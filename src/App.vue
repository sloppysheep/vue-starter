<template>
    <div>
        <h1>Witaj w systemie do zapisów na zajęcia</h1>

        <div v-show="authenticatedUsername">
            <logout-form :username="authenticatedUsername" @logout="logMeOut()" button-label></logout-form>
            <meeting-page :username="authenticatedUsername"></meeting-page>
        </div>

        <div v-if="!authenticatedUsername">
            <login-form @login="logMeIn($event)"button-label></login-form>
        </div>

    </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import LogoutForm from "./LogoutForm";
    import MeetingPage from "./meetings/MeetingPage";
    export default {
        components: {LoginForm, LogoutForm, MeetingPage},
        data() {
            return {
                authenticatedUsername: '',
            }
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