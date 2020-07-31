<template>
  <div class="add-todo">
    <form @submit="addTodo">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add a new to-do"
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuidv4(),
        title: this.title,
        completed: false,
      };
      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  background-color: #2f3236;
  padding: 1rem;
  border: 2px solid #2f3236;
  border-radius: 20px;
  min-width: 100%;
}
input[type="text"]:focus {
  border: 2px solid #73757a;
}
.btn {
  background-color: #266ce0;
  padding-left: 2rem;
  padding-right: 2rem;
  align-self: center;
  margin-left: -110px;
  height: 2.5rem;
  border: 0;
  border-radius: 20px;
  cursor: pointer;
  color: #f0f0f4;
}
</style>
