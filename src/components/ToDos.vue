<template>
  <div @click="getTodos" class="todoHead">todo's</div>
  <ul class="single-todo" v-for="todo in todoLists" :key="todo.id">
    <li>{{ todo.title }}</li>
    <button @click="editTodo(todo.id)">Edit</button>
    <button @click="deleteTodo(todo.id)">Delete</button>
  </ul>
</template>

<script>
import axios from "axios";

export default {
  name: "ToDos",
  data() {
    return {
      todoLists: [],
    };
  },
  methods: {
    // get all the todo
    getTodos() {
      axios
        .get("https://jsonplaceholder.typicode.com/todos")
        .then((res) => {
          this.todoLists = res.data.slice(
            res.data.length - 10,
            res.data.length
          );
        })
        .catch((err) => console.log(err));
    },

    // update or edit a todo
    editTodo(id) {
      axios
        .patch(`https://jsonplaceholder.typicode.com/posts/${id}`)
        .then((res) => {
          console.log(res);
        })
        .catch((err) => console.log(err));
    },

    // delete a to do
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
        .then((res) => {
          console.log(res);
          if (res.status) {
            alert("post deleted successfully" + " " + id);
          }
        })
        .catch((err) => console.log(err));
    },
  },
  beforeMount() {
    this.getTodos();
  },
};
</script>

<style scoped>
.todoHead {
  text-transform: uppercase;
  font-weight: 700;
  border-bottom: 1px solid black;
  margin-top: 2rem;
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
}
.single-todo {
  display: flex;
  gap: 0.2rem;
}
</style>
