<template>
  <div @click="getTodos">todo's</div>
  <ul v-for="todo in todoLists" :key="todo.id">
    <li>{{ todo.title }}</li>
  </ul>
</template>

<script>
import axios from "axios";

// type TodoType = {
//   title: string,
//   completed: boolean,
// };

export default {
  name: "ToDos",
  data() {
    return {
      todoLists: [],
    };
  },
  methods: {
    getTodos() {
      axios
        .get("https://jsonplaceholder.typicode.com/todos")
        .then((res) => {
          this.todoLists = res.data.slice(0, 10);
        })
        .catch((err) => console.log(err));
    },
  },
  beforeMount() {
    this.getTodos();
  },
};
</script>

<style scoped></style>
