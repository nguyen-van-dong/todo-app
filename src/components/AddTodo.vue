<template>
  <form @submit="addTodoItem">
      <input type="text" v-model="nameTodo">
      <input type="submit" value="Add">
  </form>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
    data() {
        return {
            nameTodo: ""
        }
    },
    methods: {
        addTodoItem(event) {
            event.preventDefault();
            let dataAdd = {
                id: uuidv4(),
                title: this.nameTodo,
                is_completed: false
            };
            this.nameTodo = '';
            this.$emit('add-item', dataAdd);
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
}

input[type="text"] {
    flex: 10;
    padding: 10px;
}

input[type="submit"] {
    flex: 2;
}
</style>