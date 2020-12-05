<template>
  <div class="tabela">
    <div class="entrada">
      <label for="nome">Nome:</label>
      <input type="text" v-model="nome" />
      <br /><br />
      <label for="recado">Recado:</label>
      <textarea maxlength="550" cols="30" rows="10" v-model="recado"></textarea>
      <br /><br />
      <label for="data">Data:</label>
      <input type="date" v-model="data" />
    </div>
    <div class="carta">
      <h2>{{ nome }}</h2>
      <p>{{ recado }}</p>
      <p>{{ data.split("-").reverse().join("/") }}</p>
      <br />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nome: "",
      recado: "",
      data: "",
    };
  },
};
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
  max-width: 300px;
  width: 100%;
  height: 420px;
  flex-direction: column;
  word-wrap: break-word;
  background-image: url("../assets/papel.jpg");
  background-size: 100%;
  background-repeat: no-repeat;
  font-family: "Norse", Helvetica, Arial;
  font-size: 18px;
}

textarea {
  resize: none;
}

.data {
  display: flex;
  position: absolute;
  bottom: 100px;
  right: 20%;
}

@media (max-width: 700px) {
  .tabela {
    flex-direction: column;
    align-items: center;
  }

  .entrada {
    margin-bottom: 30px;
  }
}
</style>
