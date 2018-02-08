<template>
  <div>
    <input v-model="title" placeholder="New item title"/>
    <button @click="add()">Save</button>
  </div>
</template>

<script>
  export default {
    name: 'todo-form',
    data() {
      return { title: '' }
    },
    methods: {
      add() {
        if (this.title) {
          this.$emit('add', { title: this.title });
          this.title = ''
        }
      }
    }
  }
</script>

<style>
</style>
