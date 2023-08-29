<template>
  <div class="modal" tabindex="-1">
    <div class="modal-dialog">
      <div class="modal-content" :class="{ 'bg-purple': theme === 'contact' }">
        <div class="modal-header">
          <slot name="header"></slot>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
            @click="onCloseModal"
          ></button>
        </div>
        <div class="modal-body">
          <slot />
        </div>
        <div class="modal-footer">
          <slot name="footer"></slot>
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
            @click="onCloseModal"
          >
            Close
          </button>
          <button type="button" class="btn btn-primary">Save changes</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    content: {
      type: String,
      default: "",
    },
    theme: {
      type: String,
      validator(val) {
        return ["example", "sale", "contact"].includes(val);
      },
      default: "example",
    },
  },
  data() {
    return {};
  },
  methods: {
    onCloseModal() {
      this.$emit("close");
    },
  },
};
</script>
<style lang="css">
.modal {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1060;
  display: block;
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  outline: 0;
}
.fade {
  transition: opacity 0.15s linear;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 0.5rem;
  pointer-events: none;
}
.modal-content {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 100%;
  pointer-events: auto;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 0.3rem;
  outline: 0;
}
.modal-content.bg-purple {
  background-color: #000;
}
.modal-header {
  display: flex;
  flex-shrink: 0;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 1rem;
  border-bottom: 1px solid #dee2e6;
  border-top-left-radius: calc(0.3rem - 1px);
  border-top-right-radius: calc(0.3rem - 1px);
}
</style>
