<template>
  <div class="addlist">
    <div class="lista">
      <div class="top"><h2>Cadastro de imóveis</h2></div>
      <div class="center">
        <div class="nome">Nomes:</div>
        <input
          type="text"
          v-model.trim="nomeInput"
          v-bind:class="{ borda: isBorda }"
        />
        <div
          class="neutro"
          v-if="aparecertexto"
          v-bind:class="{ error: isError }"
        >
          {{ TextoPequeno }}
        </div>
        <br />
        <div class="nome">Email:</div>
        <input
          type="email"
          v-model.trim="emailInput"
          v-bind:class="{ borda2: isBorda2 }"
        />
        <div
          class="neutro"
          v-if="aparecertexto2"
          v-bind:class="{ error2: isError2 }"
        >
          {{ TextoPequeno2 }}
        </div>
        <br />
        <div class="nome">Tipo de imóvel:</div>
        <select v-model="Tipo">
          <option disabled value="">Escolha um tipo de imóvel</option>
          <option>Casa</option>
          <option>Apartamento</option>
          <option>Comercial</option></select>
          <br />
        <div class="nome">Quartos:</div>
        <select v-model="Quartos">
          <option disabled value="">Escolha numero de quartos</option>
          <option>1</option>
          <option>2</option>
          <option>3</option>
          <option>4</option>
        </select>
        <div class="botao">
          <button @click="add">Adicionar</button>
        </div>
        <div class="resultado">{{ TotalTexto }}</div>
      </div>
    </div>
    <div class="central">
      <div class="ticket" v-for="(lista, index) in todos" :key="lista">
        <div class="coluna">
          <div class="imagem-ticket"></div>
          <div class="linha">
            <div class="resul" v-for="(value, name) in lista" :key="value">
              <p>{{ name }} : {{ value }}</p>
            </div>
          </div>
          <div class="botaoExcluir">
            <button @click="botaoExcluir(index)">Excluir</button>
          </div>
        </div>
      </div>
    </div>
    <section>
      <div class="modal" v-if="modal">
        <h3>Cadastrado com sucesso!</h3>
        <div class="confirm"></div>
        <button class="fechar" @click="fecharConfirm">Ok</button>
      </div>
      <div class="modal" v-if="modalFail">
        <h3>Erro ao cadastrar!</h3>
        <div class="fail"></div>
        <button class="fechar" @click="fecharFail">Ok</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nomeInput: "",
      emailInput: "",
      descricaof: "",
      todos: [],
      aparecer: true,
      aparecertexto: false,
      aparecertexto2: false,
      isError: false,
      isBorda: false,
      isError2: false,
      isBorda2: false,
      modal: false,
      modalFail: false,
      TextoPequeno: "Mínimo 6 caracteres",
      TextoPequeno2: "Mínimo 6 caracteres",
    };
  },
  methods: {
    add: function () {
      if (this.nomeInput.length >= 6 && this.emailInput.length >= 6) {
        this.modal = true;

        this.isError = false;
        this.isBorda = false;
        this.isError2 = false;
        this.isBorda2 = false;
        this.aparecertexto = false;
        this.aparecertexto2 = false;
      } else if (this.nomeInput.length < 6 && this.emailInput.length < 6) {
        this.modalFail = true;

        this.isError = true;
        this.isBorda = true;
        this.isError2 = true;
        this.isBorda2 = true;
        this.aparecertexto = true;
        this.aparecertexto2 = true;
      }
    },
    fecharConfirm: function () {
      this.modal = false;

      const lista = {
        Nome: this.nomeInput,
        Email: this.emailInput,
        Tipo: this.Tipo,
        Quartos: this.Quartos,
      };

      this.todos.unshift(lista);

      this.nomeInput = "";
      this.emailInput = "";
    },
    fecharFail: function () {
      this.modalFail = false;
    },
    botaoExcluir: function (index) {
      this.todos.splice(index, 1);
    },
  },
  computed: {
    TotalTexto: function () {
      return "Total de cadastros: " + this.todos.length;
    },
  },
  watch: {
    nomeInput: function () {
      if (this.nomeInput.length >= 6) {
        this.isError = false;
        this.isBorda = false;
      }
    },

    emailInput: function () {
      if (this.emailInput.length >= 6) {
        this.isError2 = false;
        this.isBorda2 = false;
      }
    },
  },
};
</script>

<style scoped>
.addlist {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  width: 100%;
  height: 100%;
  background-color: #2f3136;
}

.lista {
  display: flex;
  flex-direction: column;
  width: 350px;
  padding-top: 15px;
  height: 100vw;
  background-color: #202225;
}

@media (max-width: 630px) {
  .addlist {
    display: flex;
    flex-direction: column;
  }

  .lista {
    display: flex;
    width: 100%;
    height: 100%;
  }
}

.top {
  display: flex;
  color: white;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 20%;
}

.center {
  display: flex;
  flex-direction: column;
  padding: 6%;
  height: 100%;
  background-color: #202225;
}

.nome {
  display: flex;
  color: white;
  justify-content: flex-start;
}

#nome {
  display: flex;
  color: white;
  justify-content: flex-start;
}

.central {
  display: grid;
  width: 100%;
  height: 100%;
  padding: 20px;
  padding-bottom: 0;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  grid-template-rows: repeat(auto-fit, 1fr);
  grid-gap: 20px;
  justify-items: center;
}

.ticket {
  display: flex;
  color: white;
  flex-direction: column;
  max-width: 400px;
  width: 100%;
  height: 400px;
  border-radius: 4px;
  background-color: #4d5259;
}

.ticket ul {
  display: flex;
  flex-direction: column;
}

.ticket ul li {
  display: flex;
  list-style: none;
}

.imagem-ticket {
  display: flex;
  width: 100%;
  height: 45%;
  background-color: #bac7d9;
}

.resultado {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  width: 100%;
  height: 50px;
  color: white;
}

.botao {
  display: flex;
  margin-top: 25px;
}

.neutro {
  display: flex;
  color: white;
  justify-content: flex-start;
}

.error {
  color: red;
}

.error2 {
  color: red;
}

.white {
  color: white;
}

.borda {
  border: 2px solid red;
}

.borda2 {
  border: 2px solid red;
}

.coluna {
  display: flex;
  width: 100%;
  height: 100%;
  flex-direction: column;
  justify-content: space-around;
}

.linha {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 5%;
  overflow: hidden;
}

.resul {
  display: flex;
  width: 100%;
  height: 40px;
  align-items: flex-start;
  justify-content: center;
  flex-direction: column;
}

.item {
  display: flex;
}

textarea {
  resize: none;
}

.modal {
  display: flex;
  flex-direction: column;
  width: 250px;
  height: 250px;
  background-color: #4d5259;
  border: 1px solid #ffff;
  border-radius: 4px;
  position: absolute;
  padding: 1%;
  left: 50%;
  top: 30%;
  align-items: center;
  transform: translateX(-50%);
}

.modal h3 {
  display: flex;
  color: white;
}

.confirm {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background-image: url(../assets/confirm.png);
  background-repeat: no-repeat;
  background-size: 50%;
  background-position: center;
}

.fail {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  background-image: url(../assets/fail.png);
  background-repeat: no-repeat;
  background-size: 50%;
  background-position: center;
}

.fechar {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 50px;
}

.botaoExcluir {
  display: flex;
  height: 40px;
  padding: 2%;
  justify-content: flex-end;
}
</style>