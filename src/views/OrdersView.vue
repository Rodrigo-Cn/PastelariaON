<template>
  <div class="order">
    <h1>Gerenciar Pedidos</h1>
    <DashboardComponent/>
  </div>
</template>
<script>
  import DashboardComponent from '../components/DashboardComponent.vue';

  export default{
    name:'OrderView', 
    components:{
      DashboardComponent
    }
  }
</script>
<style>
  .order{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-top: 2%;
    padding-bottom: 2%;
  }
</style>
