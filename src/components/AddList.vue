<template>
    <div class="addlist">
        <div class="lista">
            <div class="top"><h1>Lista</h1></div>
            <div class="center">
                <div class="nome">Nomes:</div>
                <input type="text" v-model="nomeInput" v-bind:class="{ borda:isBorda}">
                <div class="neutro" v-if="aparecertexto" v-bind:class="{ error:isError }">{{ TextoPequeno }}</div>
                <div class="nome">Email:</div>
                <input type="email" v-model="emailInput" v-bind:class="{ borda2:isBorda2}">
                <div class="neutro" v-if="aparecertexto2" v-bind:class="{ error2:isError2 }">{{ TextoPequeno2 }}</div>
                <div class="botao">
                    <button v-if="aparecer" @click="add">Adicionar</button>
                </div>
            </div>
            <div class="fooooter">
                <div class="row">
                    <div>
                        <h3>Nome</h3>
                        <ul>
                            <li v-for="items in lista" :key="items">{{ items }}</li>
                        </ul>

                    </div>
                    <div>
                        <h3>Email</h3>
                        <ul>
                            <li v-for="email in emails" :key="email">{{ email }}</li>
                        </ul>

                    </div>
                </div>
                <div class="resultado">{{ TotalTexto }}</div>
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
            emails: [],
            lista: [],
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
                this.lista.push(this.nomeInput);
                this.emails.push(this.emailInput);
                
                

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
            return 'Total da lista: ' + this.lista.length;

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
    justify-content: center;
    
}

.lista {
    display: flex;
    flex-direction: column;
    min-width: 500px;
    margin: 30px;
    width: 100%;
    height: 500px;
    background-color: brown;
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
    padding: 10%;
    height: 30%;
    background-color: blue;
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

.fooooter {
    display: flex;
    color: white;
    flex-direction: column;
    width: 100%;
    height: 50%;
    background-color: rgb(101, 20, 155);
}

.fooooter ul {
    display: flex;
    flex-direction: column;
}

.fooooter ul li {
    display: flex;
    list-style: none;
}

.resultado {
    display: flex;
    margin: 30px;
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
    border: 1px solid red;
}

.borda2 {
    border: 1px solid red;
}

.row {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
}

</style>