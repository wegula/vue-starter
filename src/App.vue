<template>
  <div>


    <div v-if="authenticatedUsername">
      <h1>System zapisów na zajęcia</h1>
      <h3>Witaj {{authenticatedUsername}}!<button @click="logMeOut()">Wyloguj</button></h3>

    </div>

    <div v-else>
      <h1>Witaj w systemie zapisów na zajęcia</h1>
      <h3>Zaloguj się e-mailem
      <input type="email"
             v-model="email">
      <button @click="logMeIn()">Wchodzę</button>
      </h3>
    </div>

  </div>

</template>

<script>
import "milligram";
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
