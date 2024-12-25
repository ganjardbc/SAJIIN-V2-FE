<template>
  <gh-container class="!w-full">
    <gh-container class="!fixed z-5 top-0 left-0 w-full h-[84px] bg-white dark:bg-black dark:border-gray-700">
      <gh-layout 
        align="center"
        justify="between"
        custom-class="container mx-auto h-full px-4"
      >
        <nuxt-link to="/" class="flex items-center">
          <img src="/assets/img/logo.png" alt="" style="height: 44px;">
        </nuxt-link>
        <gh-layout 
          align="center"
          justify="end"
          gap="3"
          custom-class="flex-1 !w-auto"
        >
          <!-- <div 
            class="flex flex-row items-center justify-end gap-6 mr-4"
          >
            <gh-text size="md" weight="medium">Home</gh-text>
            <gh-text size="md" weight="medium">Feature</gh-text>
            <gh-text size="md" weight="medium">Pricing</gh-text>
            <gh-text size="md" weight="medium">Service</gh-text>
            <gh-text size="md" weight="medium">About</gh-text>
          </div> -->
          <gh-layout 
            align="center"
            justify="end"
            gap="2"
            custom-class="!w-auto flex items-center"
          >
            <u-button 
              variant="ghost" 
              color="gray"
              size="xl"
              :ui="{ rounded: 'rounded-full', padding: { xl: 'px-6 py-2.5' } }"
              class="home-layout__header-login"
              @click="toLogin"
            >
              <Icon name="mdi:login" /> Login
            </u-button>
            <u-button
              size="xl"
              :ui="{ rounded: 'rounded-full', padding: { xl: 'px-6 py-2.5' } }"
              class="home-layout__header-register"
              @click="toRegister"
            >
              Get Started
            </u-button>
          </gh-layout>
        </gh-layout>
      </gh-layout>
    </gh-container>
    <slot />
  </gh-container>
</template>
<script setup lang="ts">
const router = useRouter()

function toLogin() {
  router.push('/auth/login')
}

function toRegister() {
  router.push('/auth/register')
}
</script>
<style lang="scss" scoped>
.home-layout {
  @apply w-full h-full;
  &__header {
    &-login {
      @apply px-6 py-2.5 rounded-full;
    }
    &-register {
      @apply px-6 py-2.5 rounded-full;
      @media (max-width: theme('screens.sm')) {
        @apply hidden;
      }
    }
  }
}
</style>