<template>
  <gh-container class="home-page">
    <div class="flex flex-col gap-2 items-center py-8 w-full">
      <div class="flex flex-col gap-2 items-center pb-8">
        <gh-text weight="semibold" line-height="none" class="home-page__title">
          Create your digital
        </gh-text>
        <div class="home-page__highlight">
          <gh-text weight="semibold" line-height="none" class="home-page__highlight-title">
            order management
          </gh-text>
        </div>
        <gh-text weight="semibold" line-height="none" class="home-page__title">
          and gain more customers.
        </gh-text>
      </div>
      
      <gh-text class="home-page__description">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </gh-text>

      <div class="flex flex-row gap-2 items-center py-8">
        <u-button
          size="xl"
          :ui="{ rounded: 'rounded-full', padding: { xl: 'px-8 py-4' } }"
          @click="toRegister"
        >
          Get Started
        </u-button>
        <u-button
          color="white"
          size="xl"
          :ui="{ rounded: 'rounded-full', padding: { xl: 'px-8 py-4' } }"
        >
          Contact Us
        </u-button>
      </div>
    </div>
  </gh-container>
</template>
<script setup lang="ts">
const router = useRouter()

definePageMeta({
  layout: 'home',
})

function toRegister() {
  router.push('/auth/register')
}
</script>
<style lang="scss" scoped>
.home-page {
  @apply container mx-auto flex flex-col justify-center h-[100vh];
  &__title {
    @apply text-5xl text-center;
    @media (max-width: theme('screens.sm')) {
      @apply text-3xl;
    }
  }
  &__highlight {
    @apply py-3 border-2 border-dashed border-black;
    &-title {
      @apply text-6xl text-center text-white bg-primary px-4;
      @media (max-width: theme('screens.sm')) {
        @apply text-4xl;
      }
    }
  }
  &__description {
    @apply text-[16px] text-center;
    @media (max-width: theme('screens.sm')) {
      @apply text-sm;
    }
  }
}
</style>
