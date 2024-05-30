<template>

<div>
    
    <Login_Component/>

</div>
</template>
<script>

//import Home_inbox from './components/Home_inbox.vue'
import Login_Component from './components/Login_Component.vue';
//import Login_Component from './components/Login_Component.vue';

export default {
  name: 'App',
  components: {
    Login_Component
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
