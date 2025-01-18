<template>
    <div id="table">
        <div id="head-table">
            <div>#</div>
            <div>Cliente</div>
            <div>Sabor</div>
            <div>Status</div>
            <div>Ações</div>
        </div>
        <div v-for="order in orders" :key="order.id"  id="body-table">
            <div>{{ order.id }}</div>
            <div>{{ order.name }}</div>
            <div>{{ order.flavor }}</div>
            <div>{{ order.status }}</div>
            <div><button href="" id="drop">Cancelar</button><button href="" id="confirm">Concluir</button></div>
        </div>
    </div>
</template>
<script>
    export default{
        name:'DashboardComponent',
        data(){
            return{
                orders:[]
            }
        },
        methods:{
            async getOrders() {
                const req = await fetch('http://localhost:3000/pedidos')
                this.orders = await req.json()
            }
        },
        mounted(){
            this.getOrders()
        }
    }

</script>
<style scoped>
    #table{
        width: 80%;
        margin-top: 3%;
        min-height: 400px;
    }
    #head-table{
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-around;
        font-weight: bold;
        border-bottom: 4px solid black;
        font-size: 22px;
    }
    #body-table{
        margin-top: 1%;
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-around;
        border-bottom: 1px solid black;
        font-size: 17px;
    }
    #drop{
        background-color: red;
        color: white;
    }
    #confirm{
        background-color: green;
        color: white;
    }
    #head-table div{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    #body-table div{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
</style>