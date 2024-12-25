<template>
  <div :class="`
    relative p-4 border border-solid dark:border-gray-700 rounded-md 
    ${autoCenterClass}
    ${baseClass}
  `">
    <slot />
  </div>
</template>
<script lang="ts">
import { defineComponent, computed } from 'vue'

export default defineComponent({
  name: 'Card',
  props: {
    size: {
      type: String,
      default: 'md'
    },
    autoCenter: {
      type: Boolean,
      default: true
    },
    customClass: {
      type: String,
      default: ''
    }
  },
  setup(props) {
    const baseClass = computed(() => {
      return props.customClass
    })

    const autoCenterClass = computed(() => {
      return props.autoCenter ? 'mx-auto' : ''
    })

    return {
      baseClass,
      autoCenterClass
    }
  }
})
</script>
