<template>
 <Playboard/>
</template>

<script>
import Playboard from './components/Playboard.vue'

export default {
  name: 'App',
  components: {
   Playboard
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  

}

body{
    background: #2c3e50;
    margin: 0;
    padding: 0;
    display: flex;
    min-height: 100vh;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
</style>
