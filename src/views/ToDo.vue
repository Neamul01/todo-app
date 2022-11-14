<template>
  <div class="todo">
    <h1>Todo's</h1>
    <input type="text" name="todo" id="todo" class="todo" />
    <button class="button">Add</button>
    <div>
      <ToDos />
    </div>
  </div>
</template>

<script lang="ts">
import ToDos from "@/components/ToDos.vue";
export default {
  // name:'App',
  components: {
    ToDos,
  },
};
</script>

<style>
.todo {
  padding: 0.5rem;
}
.button {
  padding: 0.5rem;
}
</style>
