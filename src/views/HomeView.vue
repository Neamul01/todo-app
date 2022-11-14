<template>
  <div class="home">
    <h2>welcome to my Todo app, hope you will enjoy the app.</h2>
    <p>To see the Todo's, please go to the 'ToDo' route</p>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

@Options({
  components: {
    HelloWorld,
  },
})
export default class HomeView extends Vue { }
</script>
