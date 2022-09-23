<template>
  <ul class="list-group w-50 m-auto border">
    <li class="list-group-item d-flex justify-content-between align-items-center" v-for="item in list" :key="item.id" v-if="list.length>0">
      <div class="custom-control custom-checkbox">
        <input type="checkbox" class="custom-control-input" :id="item.id" v-model="item.done"/>
        <label :for="item.id" class="custom-control-label" :class="item.done ? 'delete' : ''">{{ item.task }}</label>
      </div>
      <div>
      <span class="badge badge-success badge-pill" v-if="item.done"> Done</span>
      <span class="badge badge-warning badge-pill" v-else> Undone</span>
      <button type="button" class="btn btn-outline-danger" @click="deleteTask(item.id)">Delete</button>
      </div>
    </li>

    <h3 v-else class="m-5 ">Please add some tasks!</h3>

  </ul>

</template>

<script>
export default {
  name: "TodoList",
  props:{
    list: {
      type: Array,
      required: true,
      default: []
    }
  },
  methods:{
    deleteTask(idx){
      // console.log(idx)
      this.$emit('deleteTask', idx)
    }
  },
  emits:['deleteTask']
}
</script>

<style scoped lang="scss">
 .delete{
   text-decoration: line-through;
   color: grey;
   font-style: italic;
 }
</style>