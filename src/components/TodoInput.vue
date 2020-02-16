<template>
  <div>
    <div class="inputBox shadow">
      <input 
        v-model="newTodoItem"
        v-on:keypup.enter="addTodo"
        type="text" 
        placeholder="Type what you have to do"
      >
      <span class="addContainer" v-on:click="addTodo">
        <i class="addBtn fas fa-plus" aria-hidden="true"></i>
      </span>
    </div>
  </div>
</template>

<script>
  export default {
    data(){
      return{
        newTodoItem:''
      }
    },
    methods:{
      addTodo() {
        if(this.newTodoItem !==""){
          var value = this.newTodoItem && this.newTodoItem.trim();
          localStorage.setItem(value, value);
          this.clearInput();
        }
      },
      clearInput(){
        this.newTodoItem = '';
      }
    }
  }
</script>

<style lang="scss" scoped>
 .inputBox{
   background: white;
   height: 50px;
   line-height: 50px;
   border-radius: 5px;
    input{
      border-style: none;
      font-size: 0.9rem;
      &:focus{
        outline: none;
      }
    }
    .addContainer{
      float: right;
      background : linear-gradient(to right, #6478fb, #8763fb);
      width: 3rem;
      border-radius: 0 5px 5px 0;
      .addBtn{
        color: #fff;
        vertical-align: middle;
      }
    }
 }

</style>