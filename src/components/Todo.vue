<template>
  <div class="todo">
    <h1>Todo list</h1>
    <ul>
      <li v-for="item in items" v-bind:key="item.id"><todo-item :item="item" @remove="onRemoveItem" /></li>
    </ul>
  </div>
</template>

<script>
  import request from 'superagent';
  import TodoItem from './TodoItem';

  export default {
    components: { TodoItem },
    data () {
      this.items = [];

      return { items: this.items }
    },
    created: function() {
      request
        .get('https://my-json-server.typicode.com/byzg/rep_react_todo/items')
        .then(res => this.items = res.body );
    },
    methods: {
      onRemoveItem (item){
        this.items.splice(this.items.indexOf(item), 1);
      //  SOME REQUEST TO SERVER HERE
      }
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