<template>
  <div class="alert alert-secondary d-flex "  :class="onProgress? 'alert-success ':'' ">

      <div class="d-flex flex-column ">
          <h4 :class="completed !=0 ? 'text-muted': '' "><span v-if="completed !=0"><del>{{name}}</del></span><span v-else> {{name}} </span> </h4>
      <div  class="align-self-start" v-if="completed == 0">Done :

          <input type="checkbox" @change.prevent="onChange"/>
          <br>
          On Progress <input @change.prevent="()=>{onProgress =true}" type="radio"/>
      </div>

      </div>

      <div class="d-flex  ml-auto" >

      <span class="ml-auto"  @click.prevent="deleteTodo"><i class="fa text-danger fa-trash" aria-hidden="true"></i></span>
      </div>
  </div>
</template>

<script>
export default {
name:"ItemList",
props:['name','completed'],
data(){
    return{
        onProgress: false
    }
},
created(){
    console.log("completed is "+this.completed)
},
methods:{
    deleteTodo(){
       const con = confirm('Are you sure to delete')

        if(con){
            this.$emit('set-delete')
        }else{


        }

    },
    onChange(){
        this.$emit('update-todo')
    }
}
}
</script>

<style>

</style>
