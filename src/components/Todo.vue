<template>
  <div id="todo">
  </div>
</template>

<script>

  export default {
    name: 'Todo',
  }
</script>

<style lang="scss" scoped>
  .todo {
    display: flex;
    flex-direction: column;
    ul {
      display: flex;
      margin: 0 auto;
      width: 10%;
      text-align: left;
      flex-direction: column;
      li {
        display: block;
        margin: 1rem 0;
      }
    }
  }
</style>