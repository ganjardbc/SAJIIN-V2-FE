<template>
  <div class="menu-page">
    <div class="menu-page__header">
      <div class="menu-page__profile">
        <div class="menu-page__avatar">
          <img src="https://github.com/mdo.png" alt="avatar">
        </div>
        <div class="menu-page__info">
          <gh-text class="menu-page__name">John Doe</gh-text>
          <gh-text class="menu-page__email">john.doe@example.com</gh-text>
        </div>
      </div>
    </div>
    <div class="menu-page__content">
      <div class="menu-page__section">
        <gh-text class="menu-page__section-title">Account Settings</gh-text>
        <div class="menu-page__menu-items">
          <div class="menu-page__menu-item">
            <Icon name="mdi:account-outline" class="menu-page__menu-icon" />
            <gh-text>Edit Profile</gh-text>
          </div>
          <div class="menu-page__menu-item">
            <Icon name="mdi:lock-outline" class="menu-page__menu-icon" />
            <gh-text>Change Password</gh-text>
          </div>
          <div class="menu-page__menu-item">
            <Icon name="mdi:bell-outline" class="menu-page__menu-icon" />
            <gh-text>Notifications</gh-text>
          </div>
        </div>
      </div>
      
      <div class="menu-page__section">
        <gh-text class="menu-page__section-title">Store Settings</gh-text>
        <div class="menu-page__menu-items">
          <div class="menu-page__menu-item">
            <Icon name="mdi:store-outline" class="menu-page__menu-icon" />
            <gh-text>Store Information</gh-text>
          </div>
          <div class="menu-page__menu-item">
            <Icon name="mdi:cash" class="menu-page__menu-icon" />
            <gh-text>Payment Methods</gh-text>
          </div>
          <div class="menu-page__menu-item">
            <Icon name="mdi:truck-outline" class="menu-page__menu-icon" />
            <gh-text>Shipping Options</gh-text>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
definePageMeta({
  title: 'Menu',
  breadcrumb: [
    {
      label: 'Shop',
    },
    {
      label: 'Menu',
      to: '/shop/menu'
    }
  ]
})
</script>
<style lang="scss" scoped>
.menu-page {
  @apply w-[640px] flex flex-col gap-4 mx-auto;
  @media (max-width: theme('screens.sm')) {
    @apply w-full;
  }
  &__profile {
    @apply w-full flex flex-row items-center gap-4;
  }
  &__header {
    @apply w-full bg-white rounded-lg border border-gray-200 p-6 flex flex-row items-center gap-4;
  }
  &__avatar {
    @apply w-16 h-16 rounded-full bg-gray-100 flex items-center justify-center;
    img {
      @apply w-16 h-16 rounded-full;
    }
  }
  &__info {
    @apply flex flex-col gap-1;
  }
  &__name {
    @apply text-lg font-semibold text-gray-900;
  }
  &__email {
    @apply text-sm text-gray-500;
  }
  &__content {
    @apply w-full flex flex-col gap-4;
  }
  &__section {
    @apply w-full bg-white rounded-lg border border-gray-200 p-6;
  }
  &__section-title {
    @apply text-lg font-semibold text-gray-900 mb-4;
  }
  &__menu-items {
    @apply flex flex-col gap-2;
  }
  &__menu-item {
    @apply w-full flex flex-row items-center gap-3 px-4 py-3 rounded-lg hover:bg-gray-50 cursor-pointer;
  }
  &__menu-icon {
    @apply w-5 h-5 text-gray-500;
  }
}
</style>
