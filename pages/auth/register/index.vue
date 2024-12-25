<template>
  <gh-container auto-center custom-class="w-full">
    <gh-layout direction="col" gap="2">
      <gh-layout direction="col" gap="3" custom-class="pb-8">
        <gh-text size="3xl" weight="semibold">Register</gh-text>
        <div class="w-[50px] h-[4px] bg-primary rounded-md"></div>
        <gh-text size="sm" color="gray">Please fill in the form to create an account.</gh-text>
      </gh-layout>
      
      <gh-layout direction="col" gap="3" custom-class="py-2">
        <gh-layout direction="col" gap="1">
          <gh-text size="sm">Full Name</gh-text>
          <u-input 
            v-model="form.fullName" 
            placeholder="Enter your full name"
            size="xl" 
            class="w-full" 
            icon="mdi-light:account"
            :ui="{ rounded: 'rounded-full' }" />
        </gh-layout>

        <gh-layout direction="col" gap="1">
          <gh-text size="sm">Email</gh-text>
          <u-input 
            v-model="form.email" 
            type="email" 
            placeholder="Enter your email"
            size="xl" 
            class="w-full" 
            icon="mdi-light:email"
            :ui="{ rounded: 'rounded-full' }" />
        </gh-layout>

        <gh-layout direction="col" gap="1">
          <gh-text size="sm">Password</gh-text>
          <u-input 
            v-model="form.password" 
            :type="isPasswordVisible ? 'text' : 'password'" 
            placeholder="Enter your password"
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

      <gh-layout direction="col" gap="3" custom-class="py-2">
        <u-button 
          block 
          size="xl"
          :ui="{ rounded: 'rounded-full' }"
          @click="handleRegister"
        >
          Register
        </u-button>

        <!-- <gh-layout justify="center" align="center" gap="2" direction="col">
          <gh-text size="sm">Or register with</gh-text>
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

      <gh-layout gap="1" custom-class="pt-8 justify-center items-center">
        <gh-text size="sm">Already have an account?</gh-text>
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

const isPasswordVisible = ref(false)

const form = ref({
  fullName: '',
  email: '',
  password: '',
})

const router = useRouter()
const handleRegister = () => {
  router.push('/shop/dashboard')
}
</script>