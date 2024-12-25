<template>
  <div class="cashier-page">
    <div class="cashier-page__content">
      <!-- Products Section -->
      <div class="cashier-page__products">
        <div class="cashier-page__products-grid">
          <div v-for="product in filteredProducts" 
               :key="product.id" 
               class="cashier-page__products-card"
               @click="addToCart(product)">
            <img :src="product.image" :alt="product.name" class="cashier-page__products-image">
            <div class="cashier-page__products-info">
              <gh-text class="cashier-page__products-name">{{ product.name }}</gh-text>
              <gh-text class="cashier-page__products-price">${{ product.price }}</gh-text>
            </div>
          </div>
        </div>
      </div>

      <!-- Cart Section -->
      <div class="cashier-page__cart">
        <div class="cashier-page__cart-header">
          <gh-text class="cashier-page__cart-title">Cart</gh-text>
          <u-button v-if="cart.length" 
                    color="danger" 
                    size="sm" 
                    @click="clearCart"
                    :ui="{ rounded: 'rounded-full' }">
            Clear Cart
          </u-button>
        </div>

        <div class="cashier-page__cart-items">
          <div v-for="item in cart" 
               :key="item.id" 
               class="cashier-page__cart-item">
            <div class="cashier-page__cart-item-info">
              <gh-text class="cashier-page__cart-item-name">{{ item.name }}</gh-text>
              <gh-text class="cashier-page__cart-item-price">${{ item.price * item.quantity }}</gh-text>
            </div>
            <div class="cashier-page__cart-item-quantity">
              <u-button color="white" 
                        size="sm" 
                        square 
                        @click="decrementQuantity(item)"
                        :ui="{ rounded: 'rounded-full' }">
                <Icon name="mdi:minus" />
              </u-button>
              <gh-text class="cashier-page__cart-item-count">{{ item.quantity }}</gh-text>
              <u-button color="white" 
                        size="sm" 
                        square 
                        @click="incrementQuantity(item)"
                        :ui="{ rounded: 'rounded-full' }">
                <Icon name="mdi:plus" />
              </u-button>
            </div>
          </div>
        </div>

        <div class="cashier-page__cart-footer">
          <div class="cashier-page__cart-total">
            <gh-text class="cashier-page__cart-total-label">Total</gh-text>
            <gh-text class="cashier-page__cart-total-amount">${{ cartTotal }}</gh-text>
          </div>
          <u-button color="primary" 
                    size="xl" 
                    class="w-full" 
                    :disabled="!cart.length"
                    :ui="{ rounded: 'rounded-full' }">
            Process Payment
          </u-button>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
definePageMeta({
  title: 'Cashier',
  breadcrumb: [
    {
      label: 'Shop',
    },
    {
      label: 'Cashier',
      to: '/shop/cashier'
    }
  ]
})

interface CartItem {
  id: number
  name: string
  price: number
  quantity: number
}

const cart = ref<CartItem[]>([
  {
    id: 1,
    name: 'Product 1',
    price: 9.99,
    quantity: 1
  },
  {
    id: 2, 
    name: 'Product 2',
    price: 19.99,
    quantity: 2
  }
])

const cartTotal = computed(() => {
  return cart.value.reduce((total, item) => {
    return total + (item.price * item.quantity)
  }, 0)
})

const incrementQuantity = (item: CartItem) => {
  item.quantity++
}

const decrementQuantity = (item: CartItem) => {
  if (item.quantity > 1) {
    item.quantity--
  }
}

const clearCart = () => {
  cart.value = []
}

const searchQuery = ref('')

const products = ref([
  {
    id: 1,
    name: 'Product 1',
    price: 9.99,
    category: 'Category 1'
  },
  {
    id: 2,
    name: 'Product 2', 
    price: 19.99,
    category: 'Category 2'
  },
  {
    id: 3,
    name: 'Product 3',
    price: 29.99,
    category: 'Category 1'
  },
  {
    id: 4,
    name: 'Product 4',
    price: 39.99,
    category: 'Category 2'
  }
])

const filteredProducts = computed(() => {
  return products.value.filter(product => 
    product.name.toLowerCase().includes(searchQuery.value.toLowerCase()) ||
    product.category.toLowerCase().includes(searchQuery.value.toLowerCase())
  )
})

const addToCart = (product: any) => {
  const existingItem = cart.value.find(item => item.id === product.id)
  
  if (existingItem) {
    existingItem.quantity++
  } else {
    cart.value.push({
      id: product.id,
      name: product.name,
      price: product.price,
      quantity: 1
    })
  }
}

</script>
<style lang="scss" scoped>
.cashier-page {
  @apply w-full;
  &__header {
    @apply w-full flex flex-col gap-2;
  }
  &__title {
    @apply text-3xl font-semibold text-gray-900;
  }
  &__content {
    @apply w-full flex flex-row gap-4;
    @media (max-width: theme('screens.sm')) {
      @apply flex-col;
    }
  }
  &__products {
    @apply flex-1;
    &-search {
      @apply w-full mb-4;
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
    &-card {
      @apply bg-white rounded-lg shadow-sm border border-gray-200 overflow-hidden;
      &:hover {
        @apply shadow-lg;
      }
      &-content {
        @apply p-4;
      }
      &-name {
        @apply text-lg font-semibold text-gray-900;
      }
      &-category {
        @apply text-sm text-gray-500;
      }
      &-price {
        @apply text-lg font-medium text-gray-900 mt-2;
      }
      &-actions {
        @apply mt-4 flex flex-row gap-2;
      }
    }
  }
  &__cart {
    @apply w-96 bg-white rounded-lg shadow-sm border border-gray-200 p-4;
    @media (max-width: theme('screens.sm')) {
      @apply w-full;
    }
    &-header {
      @apply flex flex-row items-center justify-between mb-4;
    }
    &-title {
      @apply text-xl font-semibold text-gray-900;
    }
    &-items {
      @apply flex flex-col gap-3;
    }
    &-item {
      @apply flex flex-row items-center justify-between py-2 border-b border-gray-200;
      &:last-child {
        @apply border-b-0;
      }
    }
    &-info {
      @apply flex flex-col;
    }
    &-name {
      @apply text-sm font-medium text-gray-900;
    }
    &-price {
      @apply text-sm text-gray-500;
    }
    &-quantity {
      @apply flex flex-row items-center gap-2;
    }
    &-total {
      @apply mt-4 pt-4 border-t border-gray-200;
      &-row {
        @apply flex flex-row items-center justify-between;
      }
      &-label {
        @apply text-sm text-gray-500;
      }
      &-value {
        @apply text-lg font-semibold text-gray-900;
      }
    }
    &-actions {
      @apply mt-4 flex flex-col gap-2;
    }
  }
}
</style>