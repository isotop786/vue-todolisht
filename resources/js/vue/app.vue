<template>
    <div>
        <p>Hello</p>
        <div v-if="data.length >0">
            <div v-for="d in data" :key="d.id">
                <h3>{{d.name}}</h3>
                <p>Comleted: <input type="checkbox"  :checked="!d.completed"/></p>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
data(){
    return{
        data:null
    }
},
created(){
    axios.get('/api/items')
    .then(res=>{
        this.data = res.data
    })

    console.log(this.data)
}
}
</script>
