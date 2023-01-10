<template>
  <form @submit="addItem">
    <input type="text" placeholder="Việc mới..." v-model="title" />
    <input type="submit" value="Thêm" class="btn btn-primary" />
  </form>
</template>

<script>
import { ref } from 'vue';
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'AddTodo',
  setup(_props, context) {
    const title = ref('');

    const addItem = (e) => {
      e.preventDefault();
      const newItem = {
        id: uuidv4(),
        title: title.value,
        completed: false
      };

      context.emit('add-todo', newItem);
    };

    return {
      title,
      addItem
    };
  }
};
</script>

<style scoped lang="scss">
form {
  display: flex;
  column-gap: 10px;
  margin-bottom: 40px;
}
input[type='text'] {
  flex: 10;
  padding: 5px;
}
input[type='submit'] {
  flex: 2;
}
</style>
