<template>
  <div class="mt-4">
    <AddTodo @add-todo="addTodo" />
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todoProps="todo"
      @item-completed="markComplete"
      @delete-todo="deleteTodo"
    />
  </div>
</template>

<script>
import { ref } from 'vue';
import TodoItem from './TodoItem.vue';
import AddTodo from './AddTodo.vue';
import { v4 as uuidv4 } from 'uuid';

export default {
  components: { TodoItem, AddTodo },
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Todo',
  setup() {
    const todos = ref([
      {
        id: uuidv4(),
        title: 'Viec 1',
        completed: false
      },
      {
        id: uuidv4(),
        title: 'Viec 2',
        completed: false
      },
      {
        id: uuidv4(),
        title: 'Viec 3',
        completed: false
      }
    ]);

    const markComplete = (id) => {
      todos.value = todos.value.map((todo) => {
        if (id === todo.id) todo.completed = !todo.completed;
        return todo;
      });
    };

    const deleteTodo = (id) => {
      todos.value = todos.value.filter((todo) => todo.id !== id);
    };

    const addTodo = (todo) => {
      if (todo) {
        todos.value.push(todo);
      }
    };

    return {
      todos,
      markComplete,
      deleteTodo,
      addTodo
    };
  }
};
</script>

<style></style>
