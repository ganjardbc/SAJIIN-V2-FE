<template>
  <gh-layout class="default-layout">
    <div class="default-layout__sidebar">
      <div class="default-layout__header">
        <nuxt-link to="/" class="flex items-center">
          <img src="/assets/img/logo.png" alt="" style="height: 34px;">
        </nuxt-link>
      </div>
      <div class="default-layout__list">
        <nuxt-link 
          v-for="(item, i) in listMenu" 
          :key="i" 
          :to="item.path" 
          :class="`
            default-layout__item 
            ${isActive(item.path) ? 'default-layout__item--active' : ''}
          `">
          <Icon :name="item.icon" :class="`default-layout__icon ${isActive(item.path) ? 'default-layout__icon--active' : ''}`" />
          <gh-text :class="`default-layout__text ${isActive(item.path) ? 'default-layout__text--active' : ''}`">{{ item.name }}</gh-text>
        </nuxt-link>
      </div>
      <div class="default-layout__footer">
        <div class="default-layout__footer-avatar">
          <img src="https://github.com/mdo.png" alt="avatar">
        </div>
      </div>
    </div>
    <div class="default-layout__content">
      <div class="default-layout__content-body">
        <div class="default-layout__content-header">
          <div class="default-layout__breadcrumb">
            <u-button 
              variant="soft" 
              color="gray"
              size="xl"
              square
              :ui="{ rounded: 'rounded-full' }"
              @click="toBack">
              <Icon name="mdi:arrow-left" />
            </u-button>
            <gh-text class="default-layout__breadcrumb-title">
              {{ title }}
            </gh-text>
            <gh-text class="default-layout__breadcrumb-divider">|</gh-text>
            <u-breadcrumb divider=">" :links="links" class="default-layout__breadcrumb-links" />
          </div>
          <div class="default-layout__profile">
            <div class="default-layout__profile-info">
              <gh-text size="sm" weight="semibold" class="text-right">
                Wednesday, 24 Dec 2024
              </gh-text>
              <gh-text size="xs" color="gray-500" class="text-right">
                Admin | Store Owner
              </gh-text>
            </div>
            <div class="default-layout__profile-avatar">
              <img src="https://github.com/mdo.png" alt="avatar">
            </div>
          </div>
        </div>
        <slot />
      </div>
    </div>
  </gh-layout>
</template>
<script setup lang="ts">
const listMenu = [
  {
    name: 'Dashboard',
    icon: 'mdi:bar-chart',
    path: '/shop/dashboard'
  },
  {
    name: 'Products',
    icon: 'mdi:box-outline',
    path: '/shop/products'
  },
  {
    name: 'Orders',
    icon: 'mdi:list-box-outline',
    path: '/shop/orders'
  },
  {
    name: 'Accounting',
    icon: 'mdi:calculator',
    path: '/shop/accounting'
  },
  {
    name: 'Menu',
    icon: 'mdi:menu',
    path: '/shop/menu'
  }
]

const isActive = (path: string) => {
  return useRoute().path === path
}

const title = computed(() => {
  return useRoute().meta.title
})

const links = computed(() => {
  return useRoute().meta.breadcrumb
})

const router = useRouter()
function toBack() {
  const urlHistory = window.history.state.back
  if (urlHistory) {
    router.back()
  } else {
    router.push('/')
  }
}
</script>
<style lang="scss" scoped>
.default-layout {
  @apply w-full h-full;
  &__sidebar {
    @apply sticky top-0 h-[100vh] bg-white shadow-lg px-4;
    width: 120px;
    @media (max-width: theme('screens.lg')) {
      @apply fixed left-0 bottom-0 w-full h-[64px] px-0 z-50;
      top: unset;
    }
  }
  &__content {
    @apply py-4 px-8 flex flex-row justify-center;
    width: calc(100% - 120px);
    &-header {
      @apply w-full h-[64px] flex items-center justify-between;
      @media (max-width: theme('screens.lg')) {
        @apply rounded-none fixed top-0 left-0 w-full h-[64px] px-4 z-50 shadow-md bg-white;
      }
    }
    &-body {
      @apply w-full flex flex-col gap-4;
      @media (max-width: theme('screens.lg')) {
        @apply py-[64px];
      }
    }
    @media (max-width: theme('screens.lg')) {
      @apply w-full px-4;
    }
  }
  &__header {
    @apply w-full h-[64px] bg-white flex items-center justify-center;
    @media (max-width: theme('screens.lg')) {
      @apply hidden;
    }
  }
  &__list {
    @apply flex flex-col gap-2 justify-center;
    height: calc(100vh - 128px);
    @media (max-width: theme('screens.lg')) {
      @apply h-full flex-row gap-0;
    }
  }
  &__item {
    @apply w-full bg-white px-4 flex flex-col gap-3 items-center justify-center rounded-lg;
    height: 84px;
    &--active {
      @apply bg-vermillion-50;
      &:hover {
        @apply bg-vermillion-50 !important;
      }
    }
    @media (max-width: theme('screens.lg')) {
      @apply h-auto px-0 gap-2 rounded-none;
    }
  }
  &__icon {
    @apply text-gray-500 h-6 w-6;
    &--active {
      @apply text-vermillion-500;
    }
    @media (max-width: theme('screens.lg')) {
      @apply h-4 w-4;
    }
  }
  &__text {
    @apply text-xs text-gray-500 font-semibold;
    &--active {
      @apply text-vermillion-500;
    }
    @media (max-width: theme('screens.lg')) {
      font-size: 10px;
    }
  }
  &__item:hover {
    @apply bg-gray-100 cursor-pointer;
    &__icon {
      @apply text-gray-900;
    }
    &__text {
      @apply text-gray-900;
    }
  }
  &__footer {
    @apply w-full h-[64px] bg-white flex items-center justify-center;
    &-avatar {
      @apply flex items-center justify-center;
      img {
        @apply w-12 h-12 rounded-full border-4 border-gray-200;
        &:hover {
          @apply cursor-pointer border-vermillion-200;
        }
        @media (max-width: theme('screens.lg')) {
          @apply w-10 h-10;
        }
      }
    }
    @media (max-width: theme('screens.lg')) {
      @apply hidden;
    }
  }
  &__profile {
    @apply flex items-center justify-end gap-3 flex-1;
    &-info {
      @media (max-width: theme('screens.sm')) {
        @apply hidden;
      }
    }
    &-avatar {
      @apply flex items-center justify-center;
      img {
        @apply w-10 h-10 rounded-full border-4 border-gray-200;
        &:hover {
          @apply cursor-pointer border-vermillion-200;
        }
        @media (max-width: theme('screens.sm')) {
          @apply w-10 h-10;
        }
      }
    }
  }
  &__breadcrumb {
    @apply w-full flex items-center gap-3 flex-1;
    &-divider {
      @apply text-gray-300;
      @media (max-width: theme('screens.sm')) {
        @apply hidden;
      }
    }
    &-links {
      @media (max-width: theme('screens.sm')) {
        @apply hidden;
      }
    }
    &-title {
      @apply text-xl font-semibold;
    }
  }
}
</style>
