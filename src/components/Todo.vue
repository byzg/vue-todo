<template>
  <div class="todo">
    <h1>Todo list</h1>
    <ul>
      <li v-for="item in items" :key="item.id"><todo-item :item="item" @remove="onRemoveItem" /></li>
    </ul>
    <todo-form @add="onAddItem"></todo-form>
  </div>
</template>

<script>
  import request from 'superagent';
  import TodoItem from './TodoItem';
  import TodoForm from './TodoForm';

  export default {
    components: { TodoItem, TodoForm },
    data () {
      this.items = [];

      return { items: this.items }
    },
    // created: async function() {
    //   request
    //     .get('http://my-json-server.typicode.com/byzg/rep_react_todo/items')
    //     .then(res => this.items = res.body );
    //   // this.items = await request.get('https://my-json-server.typicode.com/byzg/rep_react_todo/items')
    // },
    created: async function() {
      this.items = (await request.get('http://my-json-server.typicode.com/byzg/rep_react_todo/items')).body
    },
    methods: {
      onRemoveItem (item){
        this.items.splice(this.items.indexOf(item), 1);
      //  SOME REQUEST TO SERVER HERE
      },
      onAddItem (params) {
        const item = Object.assign({ id: this.items[this.items.length - 1] + 1 }, params);
        this.items.push(item)
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