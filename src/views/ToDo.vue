<template>
  <div class="todo">
    <h1>Todo's</h1>
    <div class="addTodo">
      <input type="text" name="todo" id="todo" class="todo" v-model="value" />
      <button class="button" @click="addTodo">Add</button>
    </div>
    <div class="todoList">
      <ToDos />
    </div>
    <PopUpModal
      v-show="showModal"
      @close-modal="showModal = false"
      :modalData="modalData"
    />
  </div>
</template>

<script lang="ts">
import ToDos from "@/components/ToDos.vue";
import axios from "axios";
import PopUpModal from "../components/PopUpModal.vue";

export default {
  name: "App",
  components: {
    ToDos,
    PopUpModal,
  },
  data() {
    return {
      value: "",
      showModal: false,
      modalData: {
        title: "Saved Succcessfully",
        description: "Your Todo saved successfully",
      },
    };
  },
  methods: {
    addTodo() {
      axios
        .post("https://jsonplaceholder.typicode.com/todos")
        .then((res) => {
          console.log(res);
          if (res.status === 201) {
            this.showModal = true;
          }
        })
        .catch((err) => console.log(err));
      this.value = "";
    },
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
