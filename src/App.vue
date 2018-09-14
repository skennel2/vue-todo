<template>
  
  <div id="app" class = "container">
    <br>
    <AddTodoFormVue @addTodo="addTodo"></AddTodoFormVue>
    <TodoListVue v-bind:list="todoItems" 
                 @onDeleteItem="deleteTodo"
                 @onItemValueChange='changeTodo'></TodoListVue>
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
      },
      deleteTodo : function(idx){
        this.todoItems.splice(idx, 1);
      },
      changeTodo : function(idx, oldObject, newObject){
        var original = this.todoItems[idx];
        original.todo = newObject.todo;
        original.createdDate = newObject.createdDate;
        original.isFinished = newObject.isFinished;
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
  }
</style>
