<template>
  <div>
      <form action="#" @submit.prevent="addTodo">
          <div class="row">



                  <!-- <div class="col-md-3"></div> -->
                  <div class="col-md ml-3 text-center">
                      <div class="form-group">
                          <label class="h3">Add New Task</label>
<div class="input-group mb-4 ">
  <input v-model="todo" type="text" class="form-control P-3" placeholder="e.g Hit the gym"  aria-describedby="inputGroup-sizing-lg">
  <div class="input-group-append">
    <input class="btn btn-info" type="submit" id="inputGroup-sizing-lg" :disabled="!todo" value="Add Task"/>
  </div>
</div>

                      </div>

                  </div>
                  <!-- <div class="col-md-3"></div> -->
              </div>


      </form>
  </div>
</template>

<script>
export default {
name:"AddItem",
data(){
    return{
          todo:null
    }
},
methods:{
    addTodo(){
        const todo = this.todo
       this.$emit('set-todo',todo)
       this.todo = null

    }
}
}
</script>

<style>

</style>
