<template>
  <div :class="`relative ${autoCenterClass} ${baseClass}`">
    <slot />
  </div>
</template>
<script lang="ts">
import { defineComponent, computed } from 'vue'

export default defineComponent({
  name: 'Container',
  props: {
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
