<template>
    <div class="div">
        {{ apelido }}  <br>
        {{ apelidoInvertido }} <br>
        nome inverso <br>
        {{ titulo }} <br>
        {{ novoTitulo }}<br>
        {{ tituloInvertido2() }}
        <button id="botao" v-on:click="apertar">
            Toogle
        </button>
    </div>


</template>

<script>

export default {
    data() {
        return {
            apelido: 'Magnus',
            titulo: 'Titulo da pagina',
            
        }
    },
    methods: {

        apertar: function() {
            if(this.titulo == 'Novo titulo') {
                this.titulo = 'Titulo da pagina'
                
            } else {
                this.titulo = 'Novo titulo'
                
            }
        },
        tituloInvertido2: function() {
            return this.titulo.split('').join('-');
        }
    },
    computed: {
        /*  split transforma em um array, adicionando cada campo para sua letra 
            reverse ele deixa todo o array inverso "espelhado"
            join adiciona o elemento em uma string novamente
            toUpperCase para deixar todo o texto maiusculo */
        apelidoInvertido: function() {
            return this.apelido.split('').reverse().join('');
        },
        novoTitulo: function() {
            return this.titulo.toUpperCase()
        }
    }
    
   /* beforeCreate:function() {
        alert(this.nome)
    }, */
}

/*
    beforeCreate <-- Antes de criar
    created <-- elemento ja criado

    beforeMount <-- antes de renderizar o elemento
    Mounted <-- elemento renderizado

    beforeUpdate <-- antes de ser atualizado
    updated <-- ja atualizado

    beforeDestroy
    destroyed

 */
</script>

<style scoped>

    .div {
        display: flex;
        width: 100%;
        justify-content: center;
        border-bottom: 1px solid #c6c6c6;
        padding: 2%;
    }
    .botao {
        display: flex;
        width: 200px;
        height: 100px;
    }

</style>