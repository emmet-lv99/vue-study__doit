<template>
  <section>
    <ul>
      <li v-for="(todoItem, index) in propsdata" class="shadow" v-bind:key="todoItem">
        <i class="checkBtn fas fa-check"></i>
        {{ todoItem }}
        <span class="removeBtn" type="button" v-on:click="removeTodo(todoItem, index)">
          <i class="far fa-trash-alt"></i>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>
  export default {
    props: ['propsdata'],
    methods: {
      removeTodo(todoItem, index) {
        this.$emit('removeTodo', todoItem, index);
      }
    }
  }
</script>

<style lang="scss" scoped>
  ul{
    text-align: left;
    li{
      display: flex;
      min-height: 50px;
      height: 50px;
      line-height: 50px;
      margin: 0.5rem 0;
      padding: 0 0.9rem;
      background: white;
      border-radius: 5px;
      .checkBtn{
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
      }
      .removeBtn{
        margin-left: auto;
        color: #de4343;
      }
    }
  }
</style>
