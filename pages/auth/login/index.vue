<template>
  <gh-container auto-center custom-class="w-full">
    <gh-layout direction="col" gap="2">
      <gh-layout direction="col" gap="3" custom-class="pb-8">
        <gh-text size="3xl" weight="semibold">Login</gh-text>
        <div class="w-[50px] h-[4px] bg-primary rounded-md"></div>
        <gh-text size="sm" color="gray">Welcome back! Please login to your account.</gh-text>
      </gh-layout>
      
      <gh-layout direction="col" gap="3" custom-class="py-2">
        <gh-layout direction="col" gap="1">
          <gh-text size="sm">Username</gh-text>
          <u-input 
            v-model="form.username" 
            placeholder="Enter your username"
            size="xl" 
            class="w-full" 
            icon="mdi-light:account"
            :ui="{ rounded: 'rounded-full' }" />
        </gh-layout>

        <gh-layout direction="col" gap="1">
          <gh-text size="sm">Password</gh-text>
          <u-input 
            v-model="form.password" 
            placeholder="Enter your password"
            :type="isPasswordVisible ? 'text' : 'password'" 
            size="xl" 
            class="w-full" 
            icon="mdi-light:lock"
            :ui="{ rounded: 'rounded-full', icon: { trailing: { pointer: '' } } }"
          >
            <template #trailing>
              <u-button
                color="gray"
                variant="link"
                :icon="isPasswordVisible ? 'mdi-light:eye' : 'mdi-light:eye-off'"
                :padded="false"
                class="cursor-pointer"
                @click="isPasswordVisible = !isPasswordVisible"
              />
            </template>
          </u-input>
        </gh-layout>
      </gh-layout>

      <gh-layout gap="3" custom-class="py-2">
        <gh-layout gap="2" custom-class="flex-1">
          <u-checkbox v-model="form.remember" class="cursor-pointer" />
          <gh-text size="sm">Remember me</gh-text>
        </gh-layout>
        <nuxt-link to="/auth/forgot-password">
          <gh-text size="sm" weight="semibold" text-decoration="underline">Forgot password?</gh-text>
        </nuxt-link>
      </gh-layout>

      <gh-layout direction="col" gap="3" custom-class="py-2">
        <u-button 
          block 
          size="xl"
          :ui="{ rounded: 'rounded-full' }"
          @click="handleLogin"
        >
          Login
        </u-button>

        <!-- <gh-layout justify="center" align="center" gap="2" direction="col">
          <gh-text size="sm">Or login with</gh-text>
          <gh-layout gap="2" justify="center">
            <u-button 
              variant="soft" 
              color="gray"
              size="xl"
              square
              :ui="{ rounded: 'rounded-full' }">
              <Icon name="mdi:google" />
            </u-button>
            <u-button 
              variant="soft" 
              color="gray"
              size="xl"
              square
              :ui="{ rounded: 'rounded-full' }">
              <Icon name="mdi:facebook" />
            </u-button>
            <u-button 
              variant="soft" 
              color="gray"
              size="xl"
              square
              :ui="{ rounded: 'rounded-full' }">
              <Icon name="mdi:twitter" />
            </u-button>
          </gh-layout>
        </gh-layout> -->
      </gh-layout>

      <gh-layout gap="1" custom-class="flex-1 pt-8 justify-center items-center">
        <gh-text size="sm">Don't have an account?</gh-text>
        <nuxt-link to="/auth/register">
          <gh-text size="sm" weight="semibold" text-decoration="underline">
            Register
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

const isPasswordVisible = ref(false)

const form = ref({
  username: '',
  password: '',
  remember: false,
})

const router = useRouter()
const handleLogin = () => {
  router.push('/shop/dashboard')
}
</script>