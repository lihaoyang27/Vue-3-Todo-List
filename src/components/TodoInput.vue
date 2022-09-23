<template>
  <form class="w-100 d-flex justify-content-center">
    <div class="col-auto">
      <input type="text" class="form-control"  placeholder="New task..." v-model.trim="newTaskContent">
    </div>
    <div class="col-auto">
      <button type="submit" class="btn btn-primary mb-3" @click.prevent="handleClick">Add Task</button>
    </div>
    <div class="col-auto">
      <input type="text" class="form-control"  placeholder="Search task..." v-model.trim="searchContent">
    </div>
    <div class="col-auto">
      <button type="submit" class="btn btn-success mb-3" @click.prevent="handleSearch">Search</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "TodoInput",
  data(){
    return{
      newTaskContent: "",
      searchContent: ""
    }
  },
  methods:{
    handleClick(){
      if(!this.newTaskContent) return alert('Please add task content!')
      this.$emit('addNewTask', this.newTaskContent)
      this.newTaskContent = ''
    },
    handleSearch(){
      if(!this.searchContent){this.$emit('searchTask', '')}
      this.$emit('searchTask', this.searchContent)
      this.searchContent = ''
    }
  },
  emits:['addNewTask', 'searchTask'],
}
</script>

<style scoped lang="scss">

</style>