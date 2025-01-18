<template>
    <div id="banner">
        <p id="text-banner">Monte seu pedido abaixo</p>
        <img src="/img/pastel.avif" alt="" id="banner-img">
    </div>
</template>
<script>
    export default{
        name:"BannerComponent"
    }
</script>
<style>
    #banner {
    position: relative;
    width: 100%;
    height: 100vh;
    }

    #banner-img {
    width: 100%;
    height: 100%;
    }

    #text-banner {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        color: white;
        font-size: 34px;
        font-weight: bold;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
        text-align: center;
        background-color: rgba(0, 0, 0, 0.3);
        height: 6%;
        width: 30%;
    }
</style>