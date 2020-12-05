<template>
  <div id="app">
    <Topo/>
    <Recado/>
  </div>
</template>

<script>
import Recado from './components/Recado'
import Topo from './components/Topo'

export default {
  name: 'App',
  components: {
    Recado,
    Topo
  }
}
</script>

<style>
#app {
  text-align: center;
}

@font-face {
  font-family: "Norse";
  src: local("Norse"),
   url(./fonts/Norse.otf) format("truetype");
}

</style>
