<template>

  <div id="app">

    <ContactForm />

  </div>

</template>



<script>

import ContactForm from './components/ContactForm.vue';



export default {

  name: 'App',

  components: {

    ContactForm

  }

};

</script>



<style>
#app {

  font-family: Avenir, Helvetica, Arial, sans-serif;

  -webkit-font-smoothing: antialiased;

  -moz-osx-font-smoothing: grayscale;

  text-align: center;

  margin-top: 60px;

}
</style>