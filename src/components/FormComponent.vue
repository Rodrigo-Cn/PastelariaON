<template>
  <MessageComponent :message="message" :exist="exist"/>
  <div class="banner">
    <h1>Selecione o sabor do seu pastel:</h1>
    <form @submit="createPastel" id="form-flavor">
      <div id="input-pastel">
        <input type="text" v-model="name" name="name" :class="myclass" placeholder="Nome do Cliente">
        <select name="sabor" v-model="flavorId">
          <option value="">Selecione o sabor:</option>
          <option v-for="pastel in pasteis" :key="pastel.id" :value="pastel.id">{{ pastel.nome }}</option>
        </select>
      </div>
      <div id="button">
        <button type="submit">Enviar Pedido</button>
      </div>
    </form>
  </div>
</template>
<script>
import { setTimeout } from 'core-js';
import MessageComponent from './MessageComponent.vue';
export default {
  name: 'FormComponent',
  data() {
    return {
      pasteis: [],
      name: '',
      flavor: '',
      flavorId: '',
      message:'',
      myclass:'',
      exist:false,
    };
  },
  components:{
    MessageComponent
  },
  watch:{
    name(){
      if(this.name.length > 4){
        this.myclass = 'green'
      }else if(this.name.length > 0 && this.name.length <= 4){
        this.myclass = 'yellow'
      }else{
        this.myclass = ''
      }
    }
  },
  methods: {
    async getPasteis() {
      const request = await fetch("http://localhost:3000/pastéis",{
        method: "GET",
        headers: {"Content-type":"application/json"},
      });
      this.pasteis = await request.json();
      console.log(this.pasteis)
    },
    async fetchPastelDetails() {
      if (this.flavorId) {
        const request = await fetch(`http://localhost:3000/pastéis`);
        const pasteis = await request.json();
        const pastel = pasteis.find((pastel) => pastel.id === parseInt(this.flavorId));
        this.flavor = pastel.nome;
      } else {
        this.flavor = '';
      }
    },
    async createPastel(e) {
      if (!this.flavorId) {
        alert("Selecione um sabor antes de enviar o pedido.");
        return;
      }
      if (!this.name) {
        alert("Selecione seu nome antes de enviar o pedido.");
        return;
      }

      e.preventDefault();
      await this.fetchPastelDetails();
      const data = {
        name: this.name,
        flavorId: this.flavorId,
        flavor: this.flavor,
        status: 'Processando'
      };

      const dataJSON = JSON.stringify(data)

      const request = await fetch("http://localhost:3000/pedidos",{
        method: "POST",
        headers: {"Content-type":"application/json"},
        body: dataJSON
      });

      this.message = `Pedido de ${data.name} foi criado com sucesso!`
      this.exist = true
      this.name = ''
      this.flavor = ''
      this.flavorId = ''

      setTimeout(() => {
        this.exist = false
      }, 2000)
    },
  },
  mounted() {
    this.getPasteis();
  }
};
</script>
<style>
    .banner{
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content:baseline;
      align-items: center;
      min-height: 100vh;
      margin-top: 3%;
    }
    #form-flavor{
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    #form-flavor div{
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 3%;
    }
    #input-pastel input{
      margin-bottom: 1%;
      width: 40%;
      height: 60px;
      font-size: 30px;
    }
    #input-pastel select{
      cursor: pointer;
      color: white;
      background-color: #222;
      border-radius: 5%;
      padding: 1%;
      font-size: 100%;
    }
    #button button{
      cursor: pointer;
      color: white;
      background-color: #222;
      border-radius: 1%;
      padding: 1%;
      font-size: 100%;
    }
    .yellow{
      border-left: 10px solid yellow;
    }
    .green{
      border-left: 10px solid rgb(127, 253, 137);
    }
</style>