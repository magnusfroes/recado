<template>
  <div id="app">
    <Topo />
    <Recado />
    <Exercicio />
    <Contatos />
    <Painel />
    <AddList />
  </div>
</template>

<script>
import Topo from "./components/Topo";
import Recado from "./components/Recado";
import Exercicio from "./components/Exercicio"
import Contatos from "./components/Contatos"
import Painel from "./components/Painel"
import AddList from "./components/AddList"


export default {
  name: "App",
  components: {
    Recado,
    Topo,
    Exercicio,
    Contatos,
    Painel,
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

@font-face {
  font-family: "Norse";
  src: local("Norse"), url(./fonts/Norse.otf) format("truetype");
}
</style>
