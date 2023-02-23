<template>
  <div id="app">
    <navbar/>
    <router-view/>
  </div>
</template>

<script>
  import navbar from "./components/navbar.vue"

  export default {
    name: 'root',

    components: {
      navbar,
    }
  }

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Poppins:wght@400;500;600;700&display=swap');

body {
  height: 100vh;
  background-color: #10645d !important;
}

#app {
  font-family: 'Poppins', sans-serif;
  background-color: #132524;
}

</style>
