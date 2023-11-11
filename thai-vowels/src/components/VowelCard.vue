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
  border: 1px solid var(--color-border);
  border-radius: 8px;
  padding: 0.5rem 0.8rem;
  background: var(--color-background);
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--color-text);
  transition: all 0.2s ease;
}
</style>
