<template>
  <gh-layout class="layout-login-main-container">
    <gh-layout direction="col" custom-class="layout-login-main-container-inner">
      <slot />
      <nuxt-link to="/" class="layout-login-main-container-inner-logo">
        <img src="/assets/img/logo.png" alt="" style="height: 34px;">
      </nuxt-link>
    </gh-layout>
    <!-- <gh-layout 
      direction="col" 
      justify="center" 
      align="center"
      custom-class="flex-1 w-full h-full">
      <div class="relative w-[70%] h-[70%] bg-[url('/assets/img/login-2.jpg')] bg-no-repeat bg-center bg-contain" />
    </gh-layout>
    <gh-layout 
      direction="col"
      justify="center"
      custom-class="flex-1 layout-login-main-container bg-white"
    >
      <gh-layout direction="col" custom-class="layout-login-main-container-inner">
        <slot />
      </gh-layout>
    </gh-layout> -->
  </gh-layout>
</template>
<style>
.layout-login-main-container {
  @apply relative w-full h-[100vh] bg-gray-100 flex flex-col justify-center items-center overflow-y-auto;
  @media (max-width: theme('screens.sm')) {
    @apply p-4 bg-white overflow-y-auto;
  }
}
.layout-login-main-container-inner {
  @apply relative bg-white p-8 rounded-lg shadow-lg mx-auto;
  max-width: 480px;
  @media (max-width: theme('screens.sm')) {
    @apply w-full p-0 shadow-none;
  }
}
.layout-login-main-container-inner-logo {
  @apply flex items-center absolute top-10 right-8;
  @media (max-width: theme('screens.sm')) {
    @apply top-2 right-0;
  }
}
</style>
