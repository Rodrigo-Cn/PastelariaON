<template>
    <nav id="navbar">
        <router-link id="router-img" to="/"><img src="/img/logo.png" id="logo"></router-link>
        <router-link class="route" to="/">Home</router-link>
        <router-link class="route" to="/order">Pedidos</router-link>
    </nav>
</template>
<script>
    export default{
        name:'NavBarComponent'
    }

</script>
<style scoped>
    #navbar{
        background-color: #222;
        border-bottom: 4px solid #111;
        padding-right: 2%;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        height: 12vh;
    }
    #logo{
        width: 100%;
    }
    #router-img{
        padding-right: 2%;
        width: 8%;
    }
    .route{
        color: rgb(216, 188, 148);
        text-decoration: none;
        padding-right: 2%;
        transition: .5s;
    }
    .route:hover{
        text-decoration: underline;
    }
</style>