<template>

    <div >
        <Header/>

        <div class="container p-4 text-center mb-6">
            <AddItem @set-todo="addTodo" />
        <div v-if="data.length >0" class="flex flex-col">
            <div v-for="d in data" :key="d.id">
                <ItemList

                @update-todo="updateTodo(d.id)" @set-delete="deleteTodo(d.id)" :name="d.name" :completed="d.completed" />
             </div>
        </div>
        <div v-else>
            <p>Loading todos...</p>
        </div>
        </div>



        <Footer/>
    </div>
</template>

<script>
import ItemList from './components/ItemList'
import Header from './components/Header'
import Footer from './components/Footer'
import AddItem from './components/AddItem'
import axios from 'axios'
export default {
    name:"App",
    components:{
        ItemList,
        Header,
        Footer,
        AddItem
    },

data(){
    return{
        data:[],

    }
},
methods:{
    addTodo(todo){
        axios.post('/api/item/store',{"item":{
            "name":todo
        }})
        .then(res=>{
            console.log(res)
            this.fetchTodo()
        })
        .catch(err=>{
            console.log(err)
        })
    },
    fetchTodo(){
         axios.get('/api/items')
    .then(res=>{
        this.data = res.data
    })

    console.log(this.data)
    },

    deleteTodo(id){
        axios.delete(`/api/item/${id}`)
        .then(res=>{
            console.log(res)
            this.fetchTodo();
        })
        .catch(err=>{
            console.log(err)
        })
    },
    updateTodo(id){
        axios.put(`/api/item/${id}`,{"item":
            {
                "completed":true
            }
        })
        .then(res=>{
            console.log(res)
            this.fetchTodo();
        })
        .catch(err=>console.log(err))
    }


},
created(){
    this.fetchTodo()
},

}
</script>
