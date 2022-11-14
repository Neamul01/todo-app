<template>
  <div class="modal-overlay">
    <div class="modal">
      <!-- <div v-if="!modalData?.updateModal">
        <img class="check" alt="Check" />
        <h6>Title: {{ modalData?.title }}</h6>
        <p>{{ modalData?.description }}</p>
        <button @click="$emit('close-modal')">Close</button>
      </div> -->
      <img class="check" alt="Check" />
      <h6>Title: {{ modalData?.title }}</h6>
      <p>{{ modalData?.description }}</p>
      <button @click="$emit('close-modal')">Close</button>
      <div v-if="modalData.updateModal">
        <input
          type="text"
          name="updateModal"
          id="updateModal"
          class="updateModal"
          v-model="value"
        />
        <button class="button" @click="updateTodo(this.modaldata)">
          Update
        </button>
      </div>
      {{ this.modaldata }}
    </div>
    <div class="close">
      <img class="close-img" alt="Close" @click="$emit('close-modal')" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PopUpModal",
  props: {
    modalData: {
      type: Object,
      // default: {''},
    },
  },
  data() {
    console.log(this.data);
    return {
      value: "",
      data: this.modaldata,
    };
  },
  methods: {
    updateTodo(modaldata) {
      console.log(modaldata);
      axios
        .patch(
          `https://jsonplaceholder.typicode.com/posts/${
            this.modalData?.todo?.id
          },${{ title: this.value }}`
        )
        .then((res) => {
          console.log(res);
          if (res.status) {
            alert("Todo Updated successfully");
          }
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style>
.modal-overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  background-color: #000000da;
}
.modal {
  text-align: center;
  background-color: white;
  height: 500px;
  width: 500px;
  margin-top: 10%;
  padding: 60px 0;
  border-radius: 20px;
}
.close {
  margin: 10% 0 0 16px;
  cursor: pointer;
}

.close-img {
  width: 25px;
}

.check {
  width: 150px;
}

h6 {
  font-weight: 500;
  font-size: 28px;
  margin: 20px 0;
}
</style>
