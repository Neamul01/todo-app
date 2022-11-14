<template>
  <div class="todo">
    <h1>Todo's</h1>
    <div class="addTodo">
      <input type="text" name="todo" id="todo" class="todo" />
      <button class="button">Add</button>
    </div>
    <div class="todoList">
      <ToDos />
    </div>
  </div>
</template>

<script lang="ts">
import ToDos from "@/components/ToDos.vue";
export default {
  name: "App",
  components: {
    ToDos,
  },
};
</script>

<style>
.todo {
  padding: 0.5rem;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.button {
  padding: 0.5rem;
}
.addTodo {
  margin-bottom: 0.5rem;
  display: flex;
  gap: 0.1rem;
}
.todoList {
  display: flex;
  flex-direction: column;
  width: 45rem;
  text-align: left;
}
</style>
