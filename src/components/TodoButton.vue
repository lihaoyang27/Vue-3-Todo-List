<template>

  <div class="btn-group mt-3" role="group" aria-label="Basic example">
    <button type="button" class="btn" :class="active === 'all' ? 'btn-primary' : 'btn-secondary'" @click="handleUpdate('all')">All</button>
    <button type="button" class="btn" :class="active === 'done' ? 'btn-primary' : 'btn-secondary'" @click="handleUpdate('done')">Done</button>
    <button type="button" class="btn" :class="active === 'undone' ? 'btn-primary' : 'btn-secondary'" @click="handleUpdate('undone')">Undone</button>
  </div>

</template>

<script>
export default {
  name: "TodoButton",
  props:{
    active:{
      type: String,
      required: true,
      default: 'all'
    }
  },
  emits:['update:active'],
  methods:{
    handleUpdate(status){
      if( this.active !== status) {
        this.$emit('update:active', status)
      }
    }
  }
}
</script>

<style scoped lang="scss">

</style>