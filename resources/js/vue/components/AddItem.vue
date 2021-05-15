<template>
  <div>
      <form action="#" @submit.prevent="addTodo">
          <div class="row">



                  <!-- <div class="col-md-3"></div> -->
                  <div class="col-md ml-3 text-center">
                      <div class="form-group">
                          <label class="h3">Add New Task</label>

                    <div class="input-group mb-3">
  <input v-model="todo" type="text" class="form-control" placeholder="e.g Hit the gym"  aria-describedby="button-addon2">
  <div class="input-group-append">
    <input class="btn btn-info" type="submit" id="button-addon2" :disabled="!todo" value="Add Task"/>
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
