<template>
    <div id="message">
        <MessageComponent :message="message" :exist="exist"/>
    </div>
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
            <div  v-if="order.status == 'Enviado'"><p id="final">Finalizado</p></div>
            <div  v-else><button @click="deleteOrder(order.id)" id="drop">Cancelar</button><button @click="updateOrder(order.id)" href="" id="confirm">Concluir</button></div>
        </div>
    </div>
</template>
<script>
    import MessageComponent from './MessageComponent.vue';
    export default{
        name:'DashboardComponent',
        data(){
            return{
                orders:[],
                message:'',
                exist:false,
            }
        },
        methods:{
            async getOrders() {
                const req = await fetch('http://localhost:3000/pedidos')
                this.orders = await req.json()
            },
            async deleteOrder(id){
                const req = await fetch(`http://localhost:3000/pedidos/${id}`,{
                    method: "DELETE"
                })
                const res = req.json()
                this.getOrders()
                this.message = `Pedido ${id} cancelado com sucesso!`
                this.exist = true
                setTimeout(()=>{
                    this.exist = false
                }, 2000)
            },
            async updateOrder(id){
                const data = JSON.stringify({status:'Enviado'})
                const req = await fetch(`http://localhost:3000/pedidos/${id}`,{
                    method: "PATCH",
                    headers:{'Content-Type':'application/json'},
                    body:data
                })
                const res = await req.json()
                this.getOrders()
                this.message = `Pedido ${id} enviado!`
                this.exist = true
                setTimeout(()=>{
                    this.exist = false
                }, 2000)
            }
        },
        mounted(){
            this.getOrders()
        },
        components:{
            MessageComponent
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
        cursor: pointer;
        background-color: red;
        color: white;
    }
    #confirm{
        cursor: pointer;
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
    #message{
        width: 100%;
        padding-left: 16%;
    }
</style>