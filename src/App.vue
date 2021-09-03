<template>
  <div class="application">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Top></Top>
    <InputBox :addTodo="addTodo"></InputBox>
    <ToDoList :todos="todos" :remove="remove"></ToDoList>
    <DoneList :todos="todos" :remove="remove"></DoneList>
    <Bottom :clear="clear"></Bottom>
  </div>
</template>

<script>
import Top from './components/Top'
import InputBox from './components/InputBox'
import ToDoList from './components/ToDoList'
import Bottom from './components/Bottom'
import DoneList from './components/DoneList'
// import {nanoid} from 'nanoid'

export default {
  name: 'App',
  components: {
    Top,
    InputBox,
    ToDoList,
    DoneList,
    Bottom
  },

  data() {
    return {
      todos:
        JSON.parse(localStorage.getItem('todos')) || []
      ,
    }
  },

  methods: {
    addTodo(todoitem){
      this.todos = [...this.todos, todoitem]
    },

    remove(i){
      this.todos = this.todos.filter(todoitem => todoitem.id != i)
    },

    clear(){
      this.todos = this.todos.filter(todoitem => !todoitem.id)
    }
  },

  watch: {
    todos:{
      deep: true,
      handler(value){
        localStorage.setItem('todos', JSON.stringify(value))
      }
    }
  }
}
</script>

<style>

</style>