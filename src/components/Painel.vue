<template>
    <div id="painel">
        <div id="painel2">
            <div id="top1"><h1>Lista</h1></div>  
            <div id="bodyy">
                <div id="lateral">
                    <div id="inputt">
                        <input type="text" v-model="nomeInput">
                    </div>
                    <div v-if="nomePronto">
                        <button @click="add">Adicionar</button>
                    </div>
                </div>
                <div id="lateral2">
                    <ul>
                        <li v-for="item in lista" :key="item"> {{ item }}</li>
                    </ul>

                    {{ totalTexto }}
                </div>
            </div>
            <div id="fotterr"></div>
        </div>
        
             
    </div>
    
</template>


<script>
export default {
    data() {
        return {
            nomeInput: '',
            aviso: '',
            nomePronto: false,
            lista: [],
            timer: null
        }
    },
    watch: {
        nomeInput: function() {
            if(this.timer != null) {
                clearTimeout(this.timer);
            }

            if(this.nomeInput != '') {
                this.aviso = 'Digitando...';
                this.nomePronto = false;
                this.timer = setTimeout(this.ficarPronto, 1000);
            }
        }
    },
    methods: {
        ficarPronto: function() {
            this.aviso = '';

            if(this.nomeInput.length > 2) {
                this.nomePronto = true;
            }

        },
        add: function() {
            this.lista.push(this.nomeInput);

            this.nomeInput = '';
            this.nomePronto = false;

        }
    },
    computed: {
        totalTexto: function() {
            return 'Total de nomes: ' + this.lista.length;
        }
    }
}
</script>

<style scoped>

    #painel {
        display: flex;   
        height: 100%;
        width: 100%;
        justify-content: center;
        border-bottom: 1px solid #c6c6c6;
    }

    #painel2 {
        display: flex;
        margin: 3%;
        flex-direction: column;
        border: 1px solid #c6c6c6;
        height: 500px;
        width: 400px;
    }

    #top1 {
        display: flex;
        background-color: #c2c2c2;
        justify-content: center;
        height: 40%;
        width: 100%;
    }

    #bodyy {
        display: flex;
        height: 100%;
        width: 100%;
    }

    #lateral {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        background-color: #b1adad;
        height: 100%;
        width: 70%;
    }

    #inputt {
        display: flex;
        flex-direction: row;
        width: 150px;
    }

    #lateral2 {
        display: flex;
        flex-direction: column;
        background-color: #f3f0f0;
        height: 100%;
        width: 30%;
    }

    #lateral2 ul li {
        list-style: none;
    }

    #fotterr {
        display: flex;
        height: 20%;
        width: 100%;
        background-color: #e0dfdf;
    }

</style>