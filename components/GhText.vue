<template>
  <component :is="type" :class="customClass">
    <slot />
  </component>
</template>

<script setup lang="ts">
import { defineProps, computed } from 'vue';

const props = defineProps({
  size: {
    type: String,
    default: ''
  },
  weight: {
    type: String,
    default: 'normal'
  },
  color: {
    type: String,
    default: 'black'
  },
  darkColor: {
    type: String,
    default: 'white'
  },
  align: {
    type: String,
    default: 'left'
  },
  type: {
    type: String,
    default: 'div'
  },
  // Additional font attributes
  letterSpacing: {
    type: String,
    default: ''
  },
  lineHeight: {
    type: String,
    default: ''
  },
  textTransform: {
    type: String,
    default: ''
  },
  textDecoration: {
    type: String,
    default: ''
  },
  customClass: {
    type: String,
    default: ''
  },
});

const customClass = computed(() => {
  let classes = ''

  if (props.size) {
    classes += `text-${props.size} `
  }
  if (props.weight) {
    classes += `font-${props.weight} `
  }
  if (props.color) {
    classes += `text-${props.color} `
  }
  if (props.darkColor) {
    classes += `dark:text-${props.darkColor} `
  }
  if (props.align) {
    classes += `text-${props.align} `
  }
  if (props.letterSpacing) {
    classes += `tracking-${props.letterSpacing} `
  }
  if (props.lineHeight) {
    classes += `leading-${props.lineHeight} `
  }
  if (props.textTransform) {
    classes += `${props.textTransform} `
  }
  if (props.textDecoration) {
    classes += `${props.textDecoration} `
  }
  if (props.customClass) {
    classes += `${props.customClass} `
  }

  return classes
});
</script>

<style scoped>
/* Add any additional styles if needed */
</style>