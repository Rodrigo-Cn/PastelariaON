<template>
    <div v-if="exist" class="message">
        <p>{{ message }}</p>
    </div>
</template>
<script>
    export default{
        name:'MessageComponent',
        props:{
            message:String,
            exist:Boolean
        }
    }
</script>
<style scoped>
    .message{
        width: 20%;
        margin: 2%;
        padding: 1%;
        border: 1px solid black;
        border-left: 8px solid rgb(122, 201, 221);
        background-color: azure;
    }
</style>