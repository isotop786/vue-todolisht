<template>
  <div>
      <h3 :class="completed !=0 ? 'text-muted': '' "><span v-if="completed !=0"><del>{{name}}</del></span><span v-else> {{name}} </span> <span @click.prevent="deleteTodo"><i class="fa fa-trash" aria-hidden="true"></i></span></h3>
      <p v-if="completed == 0">Done :

          <input type="checkbox" @change.prevent="onChange"/>
      </p>
  </div>
</template>

<script>
export default {
name:"ItemList",
props:['name','completed'],
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
