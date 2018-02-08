<template>
  <div class="todo-item" :class="{ 'todo-item_checked': item.checked }">
    <input type="checkbox" v-model="item.checked"/>
    <span class="todo-item__title">{{item.title}}</span>
    <button class="todo-item__remove" @click="remove()">x</button>
  </div>
</template>

<script>
  export default {
    name: 'todo-item',
    props: {
      item: {
        type: Object,
        required: true
      }
    },
    methods: {
      remove () {
        this.$emit('remove', this.item)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .todo-item {
    $scope: &;
    display: flex;
    &__remove {
      margin-left: auto
    }
    &_checked {
      #{$scope}__title {
        text-decoration: line-through;
      }
    }
  }
</style>