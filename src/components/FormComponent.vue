<template>
  <div class="banner">
    <h1>Selecione o sabor do seu pastel:</h1>
    <form action="" id="form-flavor">
      <div id="input-pastel">
        <input type="text" name="name" placeholder="Nome do Cliente">
        <select name="sabor" id="">
          <option value="">Selecione o sabor:</option>
        </select>
      </div>
      <div id="button">
        <button type="submit">Enviar Pedido</button>
      </div>
    </form>
  </div>

</template>
<script>
    export default{
        name:'FormComponent'
    }
</script>
<style>
    .banner{
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content:baseline;
      align-items: center;
      min-height: 500px;
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
      height: 40px;
      font-size: 100%;
    }
    #input-pastel select{
      cursor: pointer;
      color: white;
      background-color: #222;
      border-radius: 8%;
      padding: 1%;
      font-size: 100%;
    }
    #button button{
      cursor: pointer;
      color: white;
      background-color: #222;
      border-radius: 10%;
      padding: 1%;
      font-size: 100%;
    }
</style>