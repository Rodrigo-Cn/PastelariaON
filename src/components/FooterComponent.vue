<template>
    <div class="myfooter">
        <p>Monte o seu pastel.</p>
        <p>@Copyright 2025. Rodrigo Costa</p>
    </div>
</template>
<script>
    export default{
        name:"FooterComponent",
    }         
</script>
<style scoped>
    .myfooter{
        background-color: #222;
        border-top: 4px solid #111;
        height:200px;
        color: rgb(216, 188, 148);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
</style>