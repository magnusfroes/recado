<template>
    <div class="addlist">
        <div class="lista">
            <div class="top"><h2>Cadastro de imóveis</h2></div>
            <div class="center">
                <div class="nome">Nomes:</div>
                <input type="text" v-model="nomeInput" v-bind:class="{ borda:isBorda}">
                <div class="neutro" v-if="aparecertexto" v-bind:class="{ error:isError }">{{ TextoPequeno }}</div><br>
                <div class="nome">Email:</div>
                <input type="email" v-model="emailInput" v-bind:class="{ borda2:isBorda2}">
                <div class="neutro" v-if="aparecertexto2" v-bind:class="{ error2:isError2 }">{{ TextoPequeno2 }}</div><br>
                <div class="nome">Tipo de imóvel:</div>
                <select v-model="Tipo">
                    <option disabled value="">Escolha um tipo de imóvel</option>
                    <option>Casa</option>
                    <option>Apartamento</option>
                    <option>Comercial</option>
                </select><br>
                <div class="nome">Quartos:</div>
                <select v-model="Quartos">
                        <option disabled value="">Escolha numero de quartos</option>
                        <option>1</option>
                        <option>2</option>
                        <option>3</option>
                        <option>4</option>
                    </select>
                <div class="botao">
                    <button v-if="aparecer" @click="add">Adicionar</button>
                </div>
                <div class="resultado">{{ TotalTexto }}</div>
            </div>         
        </div>
        <div class="central"> 
            <div class="ticket"  v-for="item in todos" :key="item">
                <div class="coluna">
                    <div class="imagem-ticket"></div>
                    <div class="linha">
                        <div class="resul" v-for="(value, name) in lista" :key="value">
                            <p>{{name}} : {{ value }}</p>                                                                   
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>  
    
</template>

<script>
export default {
    data() {
        return {
            nomeInput: '',
            emailInput: '',
            descricaof: '',
            lista: {
                Nome: '',
                Email:'',
                Tipo: '',
                Quartos: ''
            },
            
            todos: [],
            aparecer: true,
            aparecertexto: false,
            aparecertexto2: false,
            isError: false,
            isBorda: false,
            isError2: false,
            isBorda2: false,
            TextoPequeno: 'Mínimo 10 caracteres',
            TextoPequeno2: 'Mínimo 10 caracteres'
        }
    },
    methods: {
        add: function() {
            if(this.nomeInput.length >= 10 && this.emailInput.length >=10) {           
                this.lista.Nome = this.nomeInput
                this.lista.Email = this.emailInput
                this.lista.Tipo = this.Tipo
                this.lista.Quartos = this.Quartos
                    
                this.todos.push(this.lista);   

                this.nomeInput = '';
                this.emailInput = '';
                /* this.aparecer = false */
                this.isError = false
                this.isBorda = false
                this.isError2 = false
                this.isBorda2 = false
                this.aparecertexto = false
                this.aparecertexto2 = false
                
            
            } else if(this.nomeInput.length < 10 && this.emailInput.length < 10) {
                this.aparecertexto = true
               
                this.isError = true
                this.isBorda = true

                this.aparecertexto2 = true
               
                this.isError2 = true
                this.isBorda2 = true

            }            
        }
    },
    computed: {
        TotalTexto: function() {
            return 'Total de cadastros: ' + this.todos.length;

        },
    },
    watch: {
        nomeInput: function() {
           /*  if(this.nomeInput.length > 1) {
                this.aparecer = true

            }  */
            if (this.nomeInput.length >= 10) {
                this.isError = false
                this.isBorda = false
            }
        },
        emailInput: function() {
            if (this.emailInput.length >= 10) {
                this.isError2 = false
                this.isBorda2 = false
            }
        },
    }
    
}
</script>

<style scoped>

.addlist {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    width: 100%;
    height: 100%;
    background-color: #2F3136;
}

.lista {
    display: flex;
    flex-direction: column;
    max-width: 280px;
    padding-top: 15px;
    width: 100%;
    height: 60vw;
    background-color: #202225;
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
    height: 80%;
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
    height: 60vw;
    padding: 20px;
    padding-bottom: 0;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: repeat(2, 1fr);
    grid-gap: 20px;
}

.ticket {
    display: flex;
    color: white;
    flex-direction: column;
    height: 100%;
    border-radius: 4px;
    background-color: #4D5259;
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
    background-color: #BAC7D9;
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
</style>