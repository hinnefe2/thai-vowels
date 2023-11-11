<script lang="ts">
import { defineComponent } from 'vue'
import thaiVowels from '../data/thai-vowels.json'
import vowelStrokes from '../data/vowel-strokes.json'
import ToggleButton from '../components/ToggleButton.vue'
import VowelCard from '../components/VowelCard.vue'
import type { VowelType } from '@/interfaces/types'

export default defineComponent({
  components: {
    ToggleButton,
    VowelCard
  },
  data() {
    return {
      activeStrokes: [] as string[],
      vowelStrokes: vowelStrokes,
      thaiVowels: thaiVowels as VowelType[],
    }
  },
  computed: {
    filteredVowels(): Array<VowelType> {
      return thaiVowels.filter((vowel: VowelType) => {
        return this.activeStrokes.every((stroke: string) => {
          return vowel.strokes.includes(stroke)
        })
      })
    }
  },
  methods: {
    addStroke(stroke: string) {
      this.activeStrokes.push(stroke)
    },
    removeStroke(stroke: string) {
      this.activeStrokes = this.activeStrokes.filter((s: string) => s !== stroke)
    },
    toggleStroke(stroke: string) {
      if (this.activeStrokes.includes(stroke)) {
        this.removeStroke(stroke)
        console.log(this.activeStrokes)
      } else {
        this.addStroke(stroke)
        console.log(this.activeStrokes)
      }
    }
  }
})
</script>

<template>
  <main>
    <section class="grid grid-2">
      <button class="pronunciation">
        <b>aa - f(a)ther</b>
      </button>
      <button class="pronunciation">
        <b>a - (A)laska</b>
      </button>
      <button class="pronunciation">
        <b>ii - s(ee)</b>
      </button>
      <button class="pronunciation">
        <b>i - t(i)p</b>
      </button>
      <button class="pronunciation">
        <b>uu - r(u)ler</b>
      </button>
      <button class="pronunciation">
        <b>u - b(oo)t</b>
      </button>
      <button class="pronunciation">
        <b>ee - p(a)le</b>
      </button>
      <button class="pronunciation">
        <b>e - p(e)t</b>
      </button>
      <button class="pronunciation">
        <b>æ, εε - s(a)d</b>
      </button>
      <button class="pronunciation">
        <b>æ, ε - c(a)t</b>
      </button>
      <button class="pronunciation">
        <b>oo - g(o)</b>
      </button>
      <button class="pronunciation">
        <b>o - n(o)te</b>
      </button>
      <button class="pronunciation">
        <b>ue, uu - r(u)ler w. a smile</b>
      </button>
      <button class="pronunciation">
        <b>oe, ɘɘ - teach(e)r</b>
      </button>
    </section>

    <div style="height: 2rem"></div>

    <section class="grid vowel-card">
      <ToggleButton
        v-for="stroke in vowelStrokes"
        :key="stroke"
        :text="stroke"
        :isActive="activeStrokes.includes(stroke)"
        @toggle="toggleStroke(stroke)"
      />
    </section>

    <div style="height: 2rem"></div>

    <section class="grid">
      <VowelCard v-for="vowel in filteredVowels" :key="vowel.thaiCharacter" :vowel="vowel" />
    </section>
  </main>
</template>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  grid-gap: 1rem;
}
.grid-2 {
  grid-template-columns: 1fr 1fr;
}
.vowel-card {
  font-family: 'Noto Sans Thai Looped', 'Noto Serif Thai', sans-serif !important;
}
button.pronunciation {
  border: 1px solid var(--color-border);
  border-radius: 8px;
  padding: 0.5rem 0.8rem;
  background: #d4e7ca;
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--color-text);
  transition: all 0.2s ease;
}
</style>
