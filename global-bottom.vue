<script setup>
import { computed } from 'vue'
import { useNav } from '@slidev/client'

// The DiracX logo, part of the template: shown on every slide,
// except the cover (which carries a large one), the full-bleed
// section dividers and the credits slide.
const { currentLayout } = useNav()
const hiddenLayouts = ['cover', 'section', 'credits']
const show = computed(() => !hiddenLayouts.includes(currentLayout.value))
</script>

<template>
  <img v-if="show" src="/public/images/diracx-logo-square.svg" class="global-logo" alt="DiracX" />
</template>
