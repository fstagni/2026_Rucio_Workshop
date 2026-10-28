<script setup>
// Local override of the neversink theme's AdmonitionType component.
// Adds a "citation" type (for quoting external reports/talks) and delegates
// all other types to the theme's original implementation.
import { computed } from 'vue'
import Admonition from 'slidev-theme-neversink/components/Admonition.vue'
import ThemeAdmonitionType from 'slidev-theme-neversink/components/AdmonitionType.vue'

const props = defineProps({
  type: {
    type: String,
    default: 'info',
  },
  width: {
    type: String,
    default: '100%',
  },
})

const admontype = computed(() => {
  if (props.type === 'citation') {
    return {
      icon: 'mdi-format-quote-open',
      title: 'Citation',
      color: 'orange-light',
    }
  }
  return null
})
</script>

<template>
  <ThemeAdmonitionType v-if="!admontype" :type="props.type" :width="props.width">
    <slot></slot>
  </ThemeAdmonitionType>
  <Admonition v-else :title="admontype.title" :color="admontype.color" :icon="admontype.icon" :width="props.width">
    <slot></slot>
  </Admonition>
</template>
