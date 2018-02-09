<template>
  <div class="todo">
    <h1>Todo list</h1>
    <ul>
      <li v-for="item in items" v-bind:key="item.id">
        <div class="todo-item">{{item.title}}</div>
      </li>
    </ul>
  </div>
</template>

<script>
  import request from 'superagent'

  export default {
    name: 'Todo',
    data() {
      return { items: [] }
    },
    created: async function () {
      this.items = (await request.get('http://my-json-server.typicode.com/byzg/rep_react_todo/items')).body
    }
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