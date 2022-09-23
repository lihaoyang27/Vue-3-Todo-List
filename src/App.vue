<script >
import TodoList from "./components/TodoList.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoButton from "./components/TodoButton.vue";

export default {
  data() {
    return {
      todoList: [
        {id: 1, task:'Monday meeting', done: true},
        {id: 2, task:'Friday dinner', done: false},
        {id: 3, task:'House work', done: false}
      ],
      nextID: 4,
      active: 'all',
      searchTerm:""
    }
  },
  components:{
    TodoList,
    TodoInput,
    TodoButton

  },
  methods:{
    addNewTask(val){
      let newTaskObj = { id: this.nextID, task: val, done: false}
      this.todoList.push(newTaskObj)
      this.nextID++
    },
    handleDelete(val){
      console.log(val)
      this.todoList = this.todoList.filter(i => i.id !== val)
    },
    handleSearch(val){
      console.log(val)
      this.searchTerm = val
    }
  },
  computed:{
    filteredList(){
      switch (this.active){
        case 'all':
          if(!this.searchTerm) {
            return this.todoList
          }else{
            return this.todoList.filter(i => i.task.toLowerCase().includes(this.searchTerm))
          }
        case 'done':
          return this.todoList.filter(i => i.done)
        case 'undone':
          return this.todoList.filter(i => !i.done)
      }
    }
  }

}
</script>


<template>
  <div class="w-100 m-auto border p-4 h-100">
    <h1>Vue-3 Todo List</h1>
    <TodoInput @addNewTask="addNewTask" @searchTask="handleSearch"></TodoInput>
    <TodoList :list="filteredList" @deleteTask="handleDelete" ></TodoList>
    <TodoButton v-model:active="active"></TodoButton>
  </div>
</template>


<style scoped lang="scss">
</style>
