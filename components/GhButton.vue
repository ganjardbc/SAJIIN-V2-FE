<template>
  <button :class="buttonClasses" @click="$emit('onClick')">
    <span v-if="iconLeft" :class="`mr-2 ${iconLeft}`"></span>
    <slot></slot>
    <span v-if="iconRight" :class="`ml-2 ${iconRight}`"></span>
  </button>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue'

export default defineComponent({
  name: 'Button',
  props: {
    variant: {
      type: String,
      default: 'primary',
      validator: (value: string) => ['primary', 'secondary', 'outline'].includes(value),
    },
    size: {
      type: String,
      default: 'lg',
      validator: (value: string) => ['sm', 'md', 'lg'].includes(value),
    },
    color: {
      type: String,
      default: 'blue',
      validator: (value: string) => ['blue', 'red', 'green', 'yellow'].includes(value),
    },
    iconLeft: {
      type: String,
      default: '',
    },
    iconRight: {
      type: String,
      default: '',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    customClass: {
      type: String,
      default: '',
    },
  },
  setup(props) {
    const buttonClasses = computed(() => {
      const baseClasses = 'inline-flex items-center justify-center font-medium rounded-full focus:outline-none';
      const variantClasses = {
        primary: 'bg-primary text-white hover:bg-primary-600',
        secondary: 'bg-gray-500 text-white hover:bg-gray-600',
        outline: 'border border-gray-500 text-gray-500 hover:bg-gray-100',
      };
      const sizeClasses = {
        sm: 'px-2 py-1 text-sm',
        md: 'px-4 py-2 text-md',
        lg: 'px-6 py-3 text-lg',
      };
      const colorClasses = {
        blue: 'text-blue-500',
        red: 'text-red-500',
        green: 'text-green-500',
        yellow: 'text-yellow-500',
      };

      if (props.disabled) {
        return `${baseClasses} ${variantClasses[props.variant]} ${sizeClasses[props.size]} ${colorClasses[props.color]} ${props.customClass} opacity-50 cursor-not-allowed`;
      } else {
        return `${baseClasses} ${variantClasses[props.variant]} ${sizeClasses[props.size]} ${colorClasses[props.color]} ${props.customClass}`;
      }
    });

    return {
      buttonClasses,
    };
  },
});
</script>

<style scoped>
/* Add any additional styles here if needed */
</style>