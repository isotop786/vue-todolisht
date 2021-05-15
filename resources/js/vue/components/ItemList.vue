<template>
  <div>
      <h3>{{name}} <span @click.prevent="deleteTodo"><i class="fa fa-trash" aria-hidden="true"></i></span></h3>
      <p>Completed: {{completed !=0 ? 'true': 'false'}}

          <input type="checkbox" :checked="completed !=0"/>
      </p>
  </div>
</template>

<script>
export default {
name:"ItemList",
props:['name','completed'],
created(){
    console.log(this.completed)
},
methods:{
    deleteTodo(){
       const con = confirm('Are you sure to delete')

        if(con){
            this.$emit('set-delete')
        }else{
            alert(0)
        }

    }
}
}
</script>

<style>

</style>
