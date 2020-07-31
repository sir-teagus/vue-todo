<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  padding: 10px;
  border-bottom: 1px dotted #f0f0f4;
}
input {
  margin-right: 10px;
}
.is-complete {
  text-decoration: line-through #f0f0f4;
}
.del {
  float: right;
  border: none;
  height: 20px;
  width: 20px;
  background-color: #2f3236;
  color: #f0f0f4;
  margin-left: 10px;
}
</style>