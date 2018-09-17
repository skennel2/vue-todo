<template>
  
  <div id="app" class = "container">
    <br>
    <AddTodoFormVue @addTodo="addTodo"></AddTodoFormVue>
    <TodoListVue v-bind:todoList="todoList" 
                 @onDeleteItem="deleteTodo"
                 @onItemValueChange='changeTodo'></TodoListVue>
    <TodoSummuryVue v-bind:todoList="todoList"></TodoSummuryVue>                
  </div>

</template>

<script>
  import AddTodoFormVue from './components/AddTodoForm.vue';
  import TodoListVue from './components/TodoList.vue';
  import TodoSummuryVue from './components/TodoSummury.vue';

  export default {
    name: 'app',
    components : {
      'AddTodoFormVue' : AddTodoFormVue,
      'TodoListVue' : TodoListVue,
      'TodoSummuryVue' : TodoSummuryVue
    },
    data () {
      return {
        todoList: []
      }
    },
    methods: {
      addTodo : function(newItem){        
        this.todoList.push(newItem);
      },
      deleteTodo : function(idx){
        this.todoList.splice(idx, 1);
      },
      changeTodo : function(idx, oldObject, newObject){
        let original = this.todoList[idx];
        original.todo = newObject.todo;
        original.modifiedDate = newObject.modifiedDate;
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
