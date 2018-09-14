<template>

  <div id="app">
    <AddTodoFormVue v-on:addTodo="addTodo"></AddTodoFormVue>
    <TodoListVue v-bind:list="todoItems"></TodoListVue>
  </div>

</template>

<script>
  import AddTodoFormVue from './components/AddTodoForm.vue';
  import TodoListVue from './components/TodoList.vue';

  export default {
    name: 'app',
    components : {
      'AddTodoFormVue' : AddTodoFormVue,
      'TodoListVue' : TodoListVue
    },
    data () {
      return {
        todoItems: []
      }
    },
    methods: {
      addTodo : function(newItem){
        this.todoItems.push(newItem);
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
  }
</style>
