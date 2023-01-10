<template>
  <div
    :class="[
      'todo-item d-flex justify-content-between',
      todoProps.completed ? 'delete' : ''
    ]"
  >
    <div class="d-flex justify-content-start align-items-center">
      <input
        type="checkbox"
        :checked="todoProps.completed"
        @change="markItemCompleted"
      />
      <p class="ms-2" @click="markItemCompleted">{{ todoProps.title }}</p>
    </div>
    <button class="btn btn-danger" @click="deleteTodo">Delete</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todoProps"],
  setup(props, context) {
    const markItemCompleted = () => {
      context.emit("item-completed", props.todoProps.id);
    };

    const deleteTodo = () => {
      context.emit("delete-todo", props.todoProps.id);
    };

    return {
      markItemCompleted,
      deleteTodo
    };
  }
};
</script>

<style lang="scss" scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  margin: 0;
  border-bottom: 1px #ccc dotted;

  &.delete {
    p {
      text-decoration: line-through;
    }
  }

  input {
    cursor: pointer;
  }

  p {
    margin-bottom: 0;
    cursor: pointer;
  }

  .btn {
    margin-left: auto;
  }
}
</style>
