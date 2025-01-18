<template>
  <div class="home">
    <BannerComponent/>
    <FormComponent/>
  </div>
</template>
<script>
  import FormComponent from '../components/FormComponent.vue';
  import BannerComponent from '../components/BannerComponent.vue';

  export default{
    name:'HomeView',
    components:{
      BannerComponent,
      FormComponent,
    },
  }

</script>
