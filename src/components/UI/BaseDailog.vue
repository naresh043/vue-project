<template>
  <teleport to="body">
    <div class="backdrop" @click.self="closeDialog"></div>
    <dialog open class="dialog">
      <div class="dialog-content">
        <header>
          <slot name="header">
            <h2>{{ title }}</h2>
          </slot>
        </header>
        <section>
          <slot></slot>
        </section>
        <menu>
          <slot name="actions">
            <base-button @click="closeDialog">Close</base-button>
          </slot>
        </menu>
      </div>
    </dialog>
  </teleport>
</template>

<script>
import BaseButton from './BaseButton.vue';

export default {
  components: {
    BaseButton
  },
  props: {
    title: {
      type: String,
      default: ''
    }
  },
  emits: ['close'],
  methods: {
    closeDialog() {
      this.$emit('close');
    }
  }
};
</script>

<style scoped>
.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.75);
  z-index: 10;
}

.dialog {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  max-width: 40rem;
  z-index: 100;
  border-radius: 12px;
  border: none;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 0;
  margin: 0;
  overflow: hidden;
  animation: modal-open 0.3s ease-out;
}

.dialog-content {
  background: white;
}

header {
  background-color: #42b983;
  color: white;
  width: 100%;
  padding: 1rem;
}

header h2 {
  margin: 0;
  font-size: 1.25rem;
}

section {
  padding: 1.5rem;
}

menu {
  padding: 1rem;
  display: flex;
  justify-content: flex-end;
  margin: 0;
  border-top: 1px solid #eee;
}

@keyframes modal-open {
  from {
    opacity: 0;
    transform: translate(-50%, -60%);
  }
  to {
    opacity: 1;
    transform: translate(-50%, -50%);
  }
}

@media (min-width: 768px) {
  .dialog {
    width: 80%;
  }
}
</style>