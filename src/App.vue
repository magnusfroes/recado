<template>
  <div id="app">
    <Topo />
    <AddList />
  </div>
</template>

<script>
import Topo from "./components/Topo";
import AddList from "./components/AddList"

export default {
  name: "App",
  components: {
    Topo,
    AddList
  },
};
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  width: 100%;
  text-align: center;
  justify-content: center;
  align-items: center;
}
</style>
