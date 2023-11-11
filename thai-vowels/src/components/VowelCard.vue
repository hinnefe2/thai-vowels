<template>
  <button class="vowel-card">
    {{ vowel.thaiCharacter }}<br />{{ vowel.transliterated }} ({{ vowel.shortLong }})
  </button>
</template>

<script lang="ts">
import { defineComponent} from 'vue'
import type { PropType } from 'vue'
import type { VowelType } from '@/interfaces/types'

export default defineComponent({
  props: {
    vowel: {
      type: Object as PropType<VowelType>,
      required: true
    }
  }
})
</script>

<style scoped>
.vowel-card {
  border: 1px solid rgba(60, 60, 60, 0.12);
  border-radius: 8px;
  padding: 0.5rem 0.8rem;
  background: #ffffff;
  font-size: 1.2rem;
  font-weight: 500;
  color: #2c3e50;
  transition: all 0.2s ease;
}
</style>
