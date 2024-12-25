<template>
  <div class="orders-page">
    <div class="orders-page__header">
      <div class="orders-page__search">
        <u-input 
          v-model="searchQuery" 
          size="xl" 
          class="w-full" 
          icon="mdi-light:magnify"
          placeholder="Search orders..."
          :ui="{ rounded: 'rounded-full', flex: { trailing: 'flex-1' } }" />
        <u-button color="primary" size="xl" :ui="{ rounded: 'rounded-full' }">
          <Icon name="mdi:plus-circle" /> Add Order
        </u-button>
      </div>
      <u-tabs :items="tabList" :default-index="0" v-model="activeTab" class="space-y-0" />
    </div>

    <div class="orders-page__content">
      <div class="orders-page__grid">
        <div v-for="order in filteredOrders" :key="order.id" class="orders-page__card">
          <div class="orders-page__card-header">
            <gh-text class="orders-page__card-id">#{{ order.id }}</gh-text>
            <div :class="[
              'orders-page__card-status',
              `orders-page__card-status--${order.status}`
            ]">
              {{ order.status }}
            </div>
          </div>
          <div class="orders-page__card-content">
            <div class="orders-page__card-info">
              <gh-text class="orders-page__card-label">Customer</gh-text>
              <gh-text class="orders-page__card-value">{{ order.customer }}</gh-text>
            </div>
            <div class="orders-page__card-info">
              <gh-text class="orders-page__card-label">Date</gh-text>
              <gh-text class="orders-page__card-value">{{ order.date }}</gh-text>
            </div>
            <div class="orders-page__card-info">
              <gh-text class="orders-page__card-label">Total</gh-text>
              <gh-text class="orders-page__card-value">${{ order.total }}</gh-text>
            </div>
          </div>
          <div class="orders-page__card-actions">
            <u-button color="white" size="md" class="w-full flex-1 flex justify-center items-center" :ui="{ rounded: 'rounded-full' }">
              <Icon name="mdi:eye" /> View Details
            </u-button>
            <u-button color="white" size="xl" square :ui="{ rounded: 'rounded-full' }">
              <Icon name="mdi:check" />
            </u-button>
          </div>
        </div>
      </div>

      <div v-if="filteredOrders.length === 0" class="orders-page__empty">
        <gh-text class="orders-page__empty-text">
          No orders found matching your search.
        </gh-text>
      </div>

      <div class="orders-page__card-empty">
        <gh-text class="orders-page__card-empty-text">
          Thats all the orders that you have.<br />
          You can add more orders by clicking the button below.
        </gh-text>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
definePageMeta({
  title: 'Orders',
  breadcrumb: [
    {
      label: 'Shop',
    },
    {
      label: 'Orders',
      to: '/shop/orders'
    }
  ]
})

interface Order {
  id: number
  customer: string
  date: string
  total: number
  status: 'pending' | 'processing' | 'completed' | 'cancelled'
}

const orders = ref<Order[]>([
  {
    id: 1,
    customer: 'John Doe',
    date: '2024-01-15',
    total: 99.99,
    status: 'completed'
  },
  {
    id: 2,
    customer: 'Jane Smith', 
    date: '2024-01-14',
    total: 149.99,
    status: 'processing'
  },
  {
    id: 3,
    customer: 'Bob Wilson',
    date: '2024-01-13', 
    total: 199.99,
    status: 'pending'
  },
  {
    id: 4,
    customer: 'Alice Brown',
    date: '2024-01-12',
    total: 249.99,
    status: 'cancelled'
  },
  {
    id: 5,
    customer: 'Alice Brown',
    date: '2024-01-12',
    total: 249.99,
    status: 'cancelled'
  },
  {
    id: 6,
    customer: 'Alice Brown',
    date: '2024-01-12',
    total: 249.99,
    status: 'cancelled'
  }
])

const searchQuery = ref('')

const filteredOrders = computed(() => {
  return orders.value.filter(order => 
    order.customer.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
    order.id.toString().includes(searchQuery.value) ||
    order.status.toLowerCase().includes(searchQuery.value.toLowerCase())
  )
})

const activeTab = ref(0)

const tabList = [
  {
    label: 'All Orders',
    value: 'all',
  },
  {
    label: 'Pending',
    value: 'pending',
  },
  {
    label: 'Processing',
    value: 'processing',
  },
  {
    label: 'Completed',
    value: 'completed',
  },
  {
    label: 'Cancelled',
    value: 'cancelled',
  }
]

const activeTabLabel = computed(() => {
  return tabList[activeTab.value].value
})
</script>
<style lang="scss" scoped>
.orders-page {
  @apply w-full;
  &__header {
    @apply w-full flex flex-col gap-4;
  }
  &__title {
    @apply text-3xl font-semibold text-gray-900;
  }
  &__content {
    @apply w-full mt-4;
  }
  &__grid {
    @apply grid grid-cols-3 gap-4;
    @media (max-width: theme('screens.md')) {
      @apply grid-cols-2;
    }
    @media (max-width: theme('screens.sm')) {
      @apply grid-cols-1;
    }
  }
  &__search {
    @apply w-full flex flex-row gap-2;
  }
  &__card {
    @apply bg-white rounded-lg shadow-sm border border-gray-200 overflow-hidden;
    &:hover {
      @apply shadow-lg;
    }
    &-header {
      @apply flex flex-row items-center justify-between p-4 border-b border-gray-200;
    }
    &-id {
      @apply text-lg font-semibold text-gray-900;
    }
    &-status {
      @apply text-sm px-3 py-1 rounded-full;
      &--pending {
        @apply bg-yellow-100 text-yellow-800;
      }
      &--processing {
        @apply bg-blue-100 text-blue-800;
      }
      &--completed {
        @apply bg-green-100 text-green-800;
      }
      &--cancelled {
        @apply bg-red-100 text-red-800;
      }
    }
    &-content {
      @apply p-4 flex flex-col gap-3;
    }
    &-info {
      @apply flex flex-row items-center justify-between;
    }
    &-label {
      @apply text-sm text-gray-500;
    }
    &-value {
      @apply text-sm text-gray-900 font-medium;
    }
    &-actions {
      @apply p-4 border-t border-gray-200 flex flex-row gap-2;
    }
  }
  &__card-empty {
    @apply w-full flex flex-row items-center justify-center pt-4;
    &-text {
      @apply text-gray-500 text-center text-sm;
    }
  }
}
</style>
