<script setup lang="ts">
import VowelCardList from './components/VowelCardList.vue'
</script>

<template>
  <main>
    <VowelCardList />
  </main>
</template>

<style scoped>

@media (min-width: 1024px) {
  .grid-item {
    flex: 0 0 calc(50% - 10px);
    margin-bottom: 20;
  }
}
@media (max-width: 767px) {
  .grid-item {
    flex: 0 0 calc(50% - 10px);
    margin-bottom: 15px;
  }
}

@media (max-width: 479px) {
  .grid-item {
    flex: 0 0 100%;
    margin-bottom: 10px;
  }
}

</style>
