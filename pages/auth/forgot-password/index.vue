<template>
  <gh-container auto-center custom-class="w-full">
    <gh-layout direction="col" gap="2">
      <gh-layout direction="col" gap="3" custom-class="pb-8">
        <gh-text size="3xl" weight="semibold">Forgot Password</gh-text>
        <div class="w-[50px] h-[4px] bg-primary rounded-md"></div>
        <gh-text size="sm" color="gray">Enter your email address and we'll send you a link to reset your password.</gh-text>
      </gh-layout>
      
      <gh-layout direction="col" gap="3" custom-class="py-2">
        <gh-layout direction="col" gap="1">
          <gh-text size="sm">Your Email</gh-text>
          <u-input 
            v-model="form.email" 
            type="email"
            placeholder="Enter your email"
            size="xl" 
            class="w-full" 
            icon="mdi-light:email"
            :ui="{ rounded: 'rounded-full' }" />
        </gh-layout>
      </gh-layout>

      <gh-layout direction="col" gap="3" custom-class="py-2">
        <u-button 
          block 
          size="xl"
          :ui="{ rounded: 'rounded-full' }"
          @click="handleForgotPassword"
        >
        Send Reset Link
        </u-button>
      </gh-layout>

      <gh-layout gap="1" custom-class="pt-8 justify-center items-center">
        <gh-text size="sm">
          Remember your password?
        </gh-text>
        <nuxt-link to="/auth/login">
          <gh-text size="sm" align="center" weight="semibold" text-decoration="underline">
            Login
          </gh-text>
        </nuxt-link>
      </gh-layout>
    </gh-layout>
  </gh-container>
</template>
<script setup lang="ts">
definePageMeta({
  layout: 'login',
})

const form = ref({
  email: '',
})

const router = useRouter()
const handleForgotPassword = () => {
  router.push('/auth/login')
}
</script>