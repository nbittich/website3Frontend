<template>
  <div>
    <nav-bar/>
    <flash-message/>
    <router-view/>
  </div>
</template>

<script>
  import NavBar from './components/Navbar'
  import FlashMessage from './components/Flash'

  export default {
    components: {NavBar, FlashMessage},
    name: 'app'
  }
</script>

<style>
  @import "https://fonts.googleapis.com/icon?family=Material+Icons";
  .card {
    border-radius: 0;
  }

  .flat {
    border-radius: 0!important;
  }
</style>
