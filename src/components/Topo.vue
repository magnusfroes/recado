<template>
    <div class="div">
        <div class="top2">
            <div class="img"></div>
            <p><strong>Magnus Froes</strong></p>
        </div>
        <h1>Imobiliaria</h1>       
    </div>
</template>

<script>
export default {
    
}
</script>

<style scoped>

.div {
    display: flex;
    width: 100%;
    color: white;
    justify-content: flex-start;
    align-items: center;
    background-color: #202225;
    border-bottom: 1px solid #2F3136;
}

.top2 {
    display: flex;
    width: 45%;
    padding-left: 10px;
    height: 100%;
    align-items: center;
    font-size: 14px;
}

h1 {
    font-family: "Norse", Helvetica, Arial;   
}

.img {
    display: flex;
    width: 50px;
    height: 50px;
    margin: 10px;
    background-image: url(../assets/perfil.jpg);
    background-size: 140%;
    background-position: center;
    background-repeat: no-repeat;
    background-color: #2F3136;
    border-radius: 50%;
}

</style>