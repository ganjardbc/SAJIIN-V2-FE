<template>
  <section :class="classes">
    <slot />
  </section>
</template>
<script setup lang="ts">
import { defineProps, computed } from 'vue';

const props = defineProps({
  layout: {
    type: String as () => 'flex' | 'grid' | 'block',
    default: 'flex'
  },
  gap: {
    type: String,
    default: '4'
  },
  direction: {
    type: String as () => 'row' | 'col',
    default: 'row'
  },
  justify: {
    type: String as () => 'start' | 'end' | 'center' | 'between' | 'around',
    default: 'start'
  },
  align: {
    type: String as () => 'start' | 'end' | 'center' | 'baseline' | 'stretch',
    default: 'start'
  },
  wrap: {
    type: String as () => 'no-wrap' | 'wrap' | 'wrap-reverse',
    default: 'no-wrap'
  },
  customClass: {
    type: String,
    default: ''
  }
})

const classes = computed(() => {
  switch (props.layout) {
    case 'flex':
      return `w-full flex gap-${props.gap} flex-${props.direction} justify-${props.justify} items-${props.align} flex-${props.wrap} ${props.customClass}`
    case 'grid':
      return `w-full grid gap-${props.gap} grid-cols-3 ${props.customClass}`
    case 'block':
      return `w-full block ${props.customClass}`
  }
})
</script>
