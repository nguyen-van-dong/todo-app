<template>
  <AddTodo @add-item="addItemTodo"/>
  <TodoItem 
      :todos="todos"
      @itemCompleted="itemIsCompleted"
      @delete-item="deleteTodoItem"
      />
</template>

<script>

import TodoItem from './TodoItem';
import AddTodo from './AddTodo';
// import { v4 as uuidv4 } from 'uuid';
import axios from 'axios'

export default {
  components: {
    TodoItem,
    AddTodo
  },
  mounted() {
    let data = this.getAllTodos();
    data.then((data) => {
      this.todos = data;
    }).catch(error => {
      console.log(error);
    })
  },
  methods: {
    itemIsCompleted(data) {
      console.log(data);
    },
    deleteTodoItem(itemTodo) {
       this.todos = this.todos.filter( (item) => item.id !== itemTodo.id);
       return this.todos;
    },
    addItemTodo(data) {
      let allItems = this.todos;
      allItems.push(data);
      this.todos = allItems;
      return this.todos;
    },
    getAllTodos: async () => {
      try {
        return await axios
              .get('https://jsonplaceholder.typicode.com/todos?_limit=10')
              .then(data => {
                return data.data;
              }).catch(error => console.log('error1: ', error));
      } catch (error) {
        console.log('error: ', error);
      }
    }
  },

  data() {
    return {
      todos: []
    }
  }
}
</script>

<style>

</style>