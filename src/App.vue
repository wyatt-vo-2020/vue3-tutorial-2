<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <h1>Welcome to Your Vue.js App</h1>
  <teleport to="body">
    <base-modal
      title="Title from Component"
      content="This is content"
      theme="sales"
      v-if="isShowModal"
      @close="onToggleModel"
    >
      <template v-slot:header>
        <h2>This is Title</h2>
      </template>
      <label for="">Name</label>
      <input type="password" />
      <template v-slot:footer>
        <h2>This is Footer</h2>
      </template>
    </base-modal>
  </teleport>
  <button @click="onToggleModel">Toggle Model</button>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  components: {
    BaseModal: Modal,
  },
  data() {
    return {
      isShowModal: false,
    };
  },
  methods: {
    onToggleModel() {
      this.isShowModal = !this.isShowModal;
    },
  },
};
</script>

<!-- <style>
</style> -->
