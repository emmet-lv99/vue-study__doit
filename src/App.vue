<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input v-on:addTodo="addTodo"></todo-input>
    <todo-list v-bind:propsdata="todoItems"></todo-list>
    <todo-footer></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  components: {
    'TodoHeader' : TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' : TodoFooter
  },
  data(){
    return{
      todoItems: []
    }
  },
  created() {
    if(localStorage.length > 0){
      for(var i = 0; i < localStorage.length; i++){
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  methods: {
    addTodo(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    }
  }

}
</script>

<style lang="scss">
// 공통요소

body {
  margin: 8px;
  font-family: 'Ubuntu', sans-serif;
  text-align: center;
  background-color: #f6f6f6;
  input{
    border-style: groove;
    width: 200px;
  }
  button{
    border-style: groove;
  }
  .shadow{
    box-shadow: 5px 10px 10px rgba(0, 0, 0, .03);
  }
}

</style>
