<template>
  <p class="todo-item" :class="{ 'is-completed': todo.is_completed }" v-for="todo in todos" :key="todo.id">
      <input type="checkbox" :checked="todo.is_completed" @click="markItemIsCompleted(todo)">
      {{ todo.title }}
      <button class="btn-delete" @click="deleteItem(todo)">Delete</button>
  </p>
</template>

<script>
export default {
    props: ['todos'],
    emits: ['item-completed'],
    data() {
        return {
            // isActive: true
        }
    },
    methods: {
        markItemIsCompleted(todo) {
            this.$emit('itemCompleted', todo);
            todo.is_completed = !todo.is_completed
        },
        deleteItem(todo) {
            this.$emit('delete-item', todo);
        }
    }

}
</script>

<style>
.todo-item {
    background: #f4f4f4;
    border-bottom: 1px #ccc dotted;
    padding: 0;
    padding: 10px;
}

.is-completed {
    text-decoration: line-through;
}

.btn-delete {
    background: red;
    color: #fff;
    border: none;
    cursor: pointer;
    float: right;
}
</style>