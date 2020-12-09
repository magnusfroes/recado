<template>
    <div class="contato">
        <div>
            <input type="text" v-model="nomeInput">
            <button @click="add">Adicionar</button>
        </div>
        <div>
            <ul>
                <li v-for="item in lista" :key="item">{{ item }}</li>
            </ul>

            <div id="totalnome">total nomes: {{ lista.length }}</div>
        </div>
        
    </div>

</template>


<script>
export default {
    data() {
        return {
            nomeInput: '',
            lista: []
        }
    },
    methods: {
        add: function() {
            if(this.nomeInput.length > 0) {
                this.lista.push(this.nomeInput);
                this.nomeInput = '';
                 if(this.lista.length > 5) {
                     /* Adicionar ou remover itens no início ou no fim do array é algo simples. As funções pop(), push(), shift() e unshift() podem ser utilizadas para isso. As duas funções iniciais manipulam itens finais do array, enquanto shift() e unshift()manipulam os elementos iniciais */
                        var totalnome = document.getElementById('totalnome');
                        this.lista.pop();
                        totalnome.style.color = "red";
                }
            } 
        }
    }
}
</script>

<style scoped>

.contato {
    display: flex;
    justify-content: center;
    width: 400px;
    height: 100%;
    flex-direction: column;
    background-color: #c6c6c6;
    padding: 2%;
    margin: 2%;
    border-bottom: 1px solid #c6c6c6;
}

ul {
    list-style: none;
}



</style>