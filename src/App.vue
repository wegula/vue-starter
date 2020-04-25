<template>
  <div>
    <h1>Witaj w systemie zapisów na zajęcia</h1>

    <div v-if="authenticatedUsername">
      <h3>Zalogowany jako: {{authenticatedUsername}}</h3>
      <button @click="logMeOut()">Wyloguj</button>
    </div>

    <div v-else>
      <p>Zaloguj się e-mailem
      <input type="email"
             v-model="email">
      <button @click="logMeIn()">Wchodzę</button>
      </p>
    </div>


  </div>

</template>

<script>
export default {
  data(){
    return{
     email:'',
     authenticatedUsername:''
    };
  },
  methods: {
    logMeIn() {
      this.authenticatedUsername = this.email;
      this.email='';
    },
    logMeOut(){
      this.authenticatedUsername='';
    }
  }
}
</script>

<style>

</style>
