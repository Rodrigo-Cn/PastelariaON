<template>
  <NavbarComponent/>
  <router-view/>
  <FooterComponent/>
</template>
<script>
  import FooterComponent from './components/FooterComponent.vue';
  import NavbarComponent from './components/NavbarComponent.vue';
  export default{
    components:{
      NavbarComponent,
      FooterComponent,
    }
  }
</script>
<style>
html, body {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: Helvetica, sans-serif;
}
</style>
