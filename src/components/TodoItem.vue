<template>
  <div class="todo-item">{{item.title}}</div>
</template>

<script>
  export default {
    name: 'TodoItem',
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