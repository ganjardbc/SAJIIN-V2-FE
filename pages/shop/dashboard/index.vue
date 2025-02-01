<template>
  <div class="dashboard-page">
    <div class="dashboard-page__content">
      <div class="dashboard-page__grid">
        <!-- main section -->
        <div class="dashboard-page__main">
          <div class="dashboard-page__main-grid">
            <div class="dashboard-page__card !bg-green-500 !border-green-500">
              <gh-layout justify="between">
                <gh-text color="white" size="md">
                  New Orders
                </gh-text>
                <gh-layout justify="center" align="center" class="!bg-white rounded-lg p-2 !w-10 !h-10">
                  <Icon name="mdi:bell-outline" class="!text-green-500" size="20" />
                </gh-layout>
              </gh-layout>
              <gh-text color="white" class="!text-5xl !font-semibold mb-2">
                16
              </gh-text>
              <gh-text color="white" size="xs">
                * Updated every new order
              </gh-text>
            </div>

            <div class="dashboard-page__card">
              <gh-layout justify="between">
                <gh-text size="md">
                  Total Orders
                </gh-text>
                <gh-layout justify="center" align="center" class="!bg-vermillion-50 rounded-lg p-2 !w-10 !h-10">
                  <Icon name="mdi:check" class="!text-vermillion-500" size="20" />
                </gh-layout>
              </gh-layout>
              <gh-text class="!text-5xl !font-semibold mb-2">
                86
              </gh-text>
              <gh-text size="xs" class="!flex items-center gap-1">
                <gh-text size="xs" color="green-500" weight="semibold">
                  +2,5%
                </gh-text>
                than usual
              </gh-text>
            </div>

            <div class="dashboard-page__card">
              <gh-layout justify="between">
                <gh-text size="md">
                  Waiting List
                </gh-text>
                <gh-layout justify="center" align="center" class="!bg-vermillion-50 rounded-lg p-2 !w-10 !h-10">
                  <Icon name="mdi:timer-outline" class="!text-vermillion-500" size="20" />
                </gh-layout>
              </gh-layout>
              <gh-text class="!text-5xl !font-semibold mb-2">
                9
              </gh-text>
              <gh-text size="xs" class="!flex items-center gap-1">
                <gh-text size="xs" color="green-500" weight="semibold">
                  +3,2%
                </gh-text>
                than usual
              </gh-text>
            </div>
          </div>
          <div class="dashboard-page__main-grid-2">
            <div class="dashboard-page__card">
              <gh-layout direction="col" class="!gap-4">
                <gh-text size="md" weight="semibold">
                  Order List
                </gh-text>
                <u-input 
                  v-model="searchQuery" 
                  size="md" 
                  class="w-full" 
                  icon="mdi-light:magnify"
                  placeholder="Search orders..."
                  :ui="{ rounded: 'rounded-full' }" />
                <gh-layout v-for="i in 10" :key="i" align="center" class="!gap-3">
                  <gh-layout justify="center" align="center" class="!bg-vermillion-100 rounded-lg p-2 !w-10 !h-10">
                    <gh-text color="vermillion-500" size="md" weight="semibold">
                      #2
                    </gh-text>
                  </gh-layout>
                  <gh-layout justify="center" align="center" class="flex-1">
                    <gh-layout direction="col" class="!gap-1">
                      <gh-text size="md" weight="semibold">
                        Ariel Hikmat
                      </gh-text>
                      <gh-text size="xs" color="gray-500">
                        4 items
                      </gh-text>
                    </gh-layout>
                    <gh-layout direction="col" align="end" class="!gap-1">
                      <u-badge color="blue" class="flex items-center gap-1">
                        <Icon name="mdi:check-circle" class="!text-white" size="16" />
                        Ready
                      </u-badge>
                      <gh-text size="xs" color="gray-500" class="flex items-center gap-1">
                        <Icon name="mdi:circle" class="!text-yellow-500" size="8" />
                        Ready to serve
                      </gh-text>
                    </gh-layout>
                  </gh-layout>
                </gh-layout>
              </gh-layout>
            </div>

            <div class="dashboard-page__card">
              <gh-layout direction="col" class="!gap-4">
                <gh-text size="md" weight="semibold">
                  Payment
                </gh-text>
                <u-input 
                  v-model="searchQuery" 
                  size="md" 
                  class="w-full" 
                  icon="mdi-light:magnify"
                  placeholder="Search payment..."
                  :ui="{ rounded: 'rounded-full' }" />
                <gh-layout v-for="i in 10" :key="i" align="center" class="!gap-3">
                  <gh-layout justify="center" align="center" class="!bg-vermillion-100 rounded-lg p-2 !w-10 !h-10">
                    <gh-text color="vermillion-500" size="md" weight="semibold">
                      AC
                    </gh-text>
                  </gh-layout>
                  <gh-layout justify="center" align="center" class="flex-1">
                    <gh-layout direction="col" class="!gap-1">
                      <gh-text size="md" weight="semibold">
                        Ariel Hikmat
                      </gh-text>
                      <gh-text size="xs" color="gray-500">
                        Order #23232
                      </gh-text>
                    </gh-layout>
                    <gh-layout direction="col" align="end" class="!gap-1">
                      <u-button color="green" size="sm" :ui="{ rounded: 'rounded-full' }">
                        Pay Now <Icon name="mdi:arrow-right" />
                      </u-button>
                    </gh-layout>
                  </gh-layout>
                </gh-layout>
              </gh-layout>
            </div>
          </div>
        </div>

        <!-- right section -->
        <div class="dashboard-page__right">
          <u-button color="primary" size="xl" block :ui="{ rounded: 'rounded-full' }">
            <Icon name="mdi:plus-circle" /> Create New Order
          </u-button>

          <div class="dashboard-page__card">
            <gh-layout justify="between" align="center" class="!mb-4">
              <gh-text size="md" weight="semibold">
                Popular Products
              </gh-text>
              <gh-text size="sm" color="vermillion-500" class="cursor-pointer">
                View All
              </gh-text>
            </gh-layout>
            <div class="dashboard-page__list">
              <gh-layout layout="grid" class="!grid-cols-6">
                <gh-text size="xs" color="gray-500" class="!col-span-1">
                  Rank
                </gh-text>
                <gh-text size="xs" color="gray-500" class="!col-span-5">
                  Name
                </gh-text>
              </gh-layout>
              <gh-layout 
                v-for="i in 4" 
                :key="i" 
                layout="grid" 
                class="dashboard-page__list-item !grid-cols-6">
                <gh-text size="sm" weight="semibold" class="!col-span-1">
                  #{{ i }}
                </gh-text>
                <gh-layout justify="center" align="center" class="!col-span-5 gap-2">
                  <div class="dashboard-page__list-image">
                    <img src="https://picsum.photos/200" alt="product">
                  </div>
                  <gh-layout direction="col" class="flex-1 !gap-1">
                    <gh-text size="sm" weight="semibold">
                      Product Name
                    </gh-text>
                    <gh-layout class="flex-1 !gap-1">
                      <gh-text size="xs" color="gray-500">
                        Orders :
                      </gh-text>
                      <gh-text size="xs" color="green-500">
                        15
                      </gh-text>
                    </gh-layout>
                  </gh-layout>
                </gh-layout>
              </gh-layout>
            </div>
          </div>

          <div class="dashboard-page__card">
            <gh-layout justify="between" align="center" class="!mb-4">
              <gh-text size="md" weight="semibold">
                Out of Stock
              </gh-text>
              <gh-text size="sm" color="vermillion-500" class="cursor-pointer">
                View All
              </gh-text>
            </gh-layout>
            <div class="dashboard-page__list">
              <gh-layout 
                v-for="i in 4" 
                :key="i" 
                direction="col" 
                gap="1"
                class="dashboard-page__list-item">
                <gh-layout justify="between" align="center" class="!gap-2">
                  <gh-text size="sm" weight="semibold">
                    Product Name
                  </gh-text>
                  <gh-text size="xs" color="gray-500">
                    SKU: #123456
                  </gh-text>
                </gh-layout>                
                <gh-layout class="flex-1 !gap-1">
                  <gh-text size="xs" color="gray-500">
                    Available :
                  </gh-text>
                  <gh-text size="xs" color="green-500">
                    16:00 PM
                  </gh-text>
                </gh-layout>
              </gh-layout>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
definePageMeta({
  title: 'Dashboard',
  breadcrumb: [
    {
      label: 'Shop',
    },
    {
      label: 'Dashboard',
      to: '/shop/dashboard'
    }
  ]
})

const searchQuery = ref('')
</script>
<style lang="scss" scoped>
.dashboard-page {
  @apply w-full;
  &__grid {
    @apply flex flex-row gap-4;
    @media (max-width: theme('screens.sm')) {
      @apply flex flex-col-reverse;
    }
  }
  &__main {
    @apply flex flex-col gap-4 flex-1;
    width: calc(100% - 300px);
    @media (max-width: theme('screens.sm')) {
      @apply w-full;
    }
    &-grid {
      @apply grid grid-cols-3 gap-4;
      @media (max-width: theme('screens.xl')) {
        @apply grid-cols-2;
      }
      @media (max-width: theme('screens.lg')) {
        @apply grid-cols-1;
      }
    }
    &-grid-2 {
      @apply grid grid-cols-2 gap-4;
      @media (max-width: theme('screens.xl')) {
        @apply grid-cols-1;
      }
    }
  }
  &__right {
    @apply flex flex-col gap-4;
    width: 300px;
    @media (max-width: theme('screens.sm')) {
      @apply flex w-full;
    }
  }
  &__card {
    @apply bg-white rounded-xl p-4 border border-gray-200;
  }
  &__list {
    @apply flex flex-col gap-4;
  }
  &__list-item {
    @apply border-b border-gray-200 pb-4 last:!border-none last:pb-0;
  }
  &__list-image {
    @apply w-10 h-10 rounded-lg overflow-hidden;
  }
}
</style>
