<template>
  <div id="app">
    <HeaderItem />
    <Todo />
  </div>
</template>

<script>
import HeaderItem from "./components/Header";
import Todo from "./components/Todo";
export default {
  name: "App",
  components: {
    HeaderItem,
    Todo
  }
};
</script>

<style></style>
