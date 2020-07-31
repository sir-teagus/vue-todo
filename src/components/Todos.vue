<template>
  <div class="myTodos">
    <div v-for="todo in todos" v-bind:key="todo.id">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "Todos",
  components: { TodoItem },
  props: ["todos"],
};
</script>

<style scoped>
.myTodos {
  background-color: #2f3236;
  margin: 40px 0px;
  padding: 20px;
  min-height: 450px;
  min-width: 100%;
  border-radius: 20px;
}
</style>