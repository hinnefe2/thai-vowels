<template>
  <button class="toggle-button grid-item" :class="{ active: isActive}" @click="toggle">
    <b>{{ text }}</b>
  </button>
</template>

<script lang="ts">
export default {
  data () {
    return {
      isActive: false
    }
  },
  props: {
    text: {
      type: String,
      required: true
    },
  },
  methods: {
    toggle () {
      this.isActive = !this.isActive;
      this.$emit('toggle');
    }
  }
}
</script>

<style scoped>
.toggle-button {
  border: 1px solid var(--color-border);
  border-radius: 8px;
  padding: 0.5rem 0.8rem;
  background: var(--color-background);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--color-text);
  transition: all 0.2s ease;
}

.toggle-button.active {
  background-color: #1fb82e;
  color: var(--color-background);
}
</style>