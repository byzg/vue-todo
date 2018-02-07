<template>
  <div>
    <h1>Todo list</h1>
    <ul>
      <li v-for="item in items" v-bind:key="item.id">{{item.title}}</li>
    </ul>
  </div>
</template>

<script>
  import request from 'superagent';

  export default {
    data () {
      this.items = [];

      return { items: this.items }
    },
    created: function() {
      request
        .get('https://my-json-server.typicode.com/byzg/rep_react_todo/items')
        .then(res => this.items = res.body );
    }
  }
</script>