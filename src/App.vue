<template>
  <div id="app">
    <Recado/>
  </div>
</template>

<script>
import Recado from './components/Recado'

export default {
  name: 'App',
  components: {
    Recado
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

@font-face {
  font-family: "Norse";
  src: local("Norse"),
   url(./fonts/Norse.otf) format("truetype");
}

</style>
