<template>
  <div>
      <h3>{{name}} <span><i></i></span></h3>
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
}
}
</script>

<style>

</style>
