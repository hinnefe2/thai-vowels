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
  border: 1px solid rgba(60, 60, 60, 0.12);
  border-radius: 8px;
  padding: 0.5rem 0.8rem;
  background: #ffffff;
  font-size: 1.2rem;
  font-weight: 500;
  color: #2c3e50;
  transition: all 0.2s ease;
}

.toggle-button.active {
  background-color: #1fb82e;
  color: #ffffff;
}
</style>