<template>
    <div>
        <h3>Witaj {{username}}!
            <button @click="logMeOut()">Wyloguj</button>
        </h3>

    </div>
</template>

<script>
    export default {
        props: ['username'],
        methods: {
            logMeOut(){
                this.$emit('logout')
            }
        }
    }
</script>

<style scoped>

</style>