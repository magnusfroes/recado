<template>
  <div class="tabela">
    <div class="entrada">
      <label for="nome">Nome:</label>
      <input type="text" v-model="nome">
      <br><br>
      <label for="recado">Recado:</label>
      <textarea cols="30" rows="10" v-model="recado"></textarea>
      <br><br>
      <label for="data">Data:</label>
      <input type="text" v-model="data">
    </div>
    <div class="carta">
      <h2>{{ nome }}</h2>
      <p>{{ recado }}</p>
      <br>
      <p>{{ data }}</p>
    </div>
  </div>
  
</template>

<script>
export default {
    data() {
      return {
        nome: '',
        recado: '',
        data: ''
      }
    }
}
</script>


<style scoped>

.entrada {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}

.tabela {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: space-around;
  width: 100%;
}
.carta {
  display: flex;
  margin: 20px;
  padding: 20px;
  width: 300px;
  height: 420px;
  flex-direction: column;
  word-wrap: break-word;
  background-image: url('../assets/papel.jpg');
  background-size: 100%;
  background-repeat: no-repeat;
  font-family: "Norse", Helvetica, Arial;
  font-size: 18px;
}
</style>
