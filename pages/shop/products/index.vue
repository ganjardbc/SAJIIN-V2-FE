<template>
  <div class="products-page">
    <div class="products-page__header">
      <div class="products-page__search">
        <u-input 
          v-model="searchQuery" 
          size="xl" 
          class="w-full" 
          icon="mdi-light:magnify"
          placeholder="Search products..."
          :ui="{ rounded: 'rounded-full', flex: { trailing: 'flex-1' } }" />
        <u-button color="primary" size="xl" :ui="{ rounded: 'rounded-full' }">
          <Icon name="mdi:plus-circle" /> Add Product
        </u-button>
      </div>
    </div>

    <div class="products-page__content">
      <div class="products-page__grid">
        <div v-for="product in filteredProducts" :key="product.id" class="products-page__card">
          <div v-if="product.isNew" class="products-page__card-badge">
            New Product
          </div>
          <div class="products-page__card-image">
            <img :src="product.image" :alt="product.name">
          </div>
          <div class="products-page__card-content">
            <gh-text class="products-page__card-title">{{ product.name }}</gh-text>
            <gh-text class="products-page__card-price">${{ product.price }}</gh-text>
            <gh-text class="products-page__card-stock">Stock: {{ product.stock }}</gh-text>
          </div>
          <div class="products-page__card-actions">
            <u-button color="white" size="md" class="w-full flex-1 flex justify-center items-center" :ui="{ rounded: 'rounded-full' }">
              <Icon name="mdi:pencil" /> Edit
            </u-button>
            <u-button color="white" size="xl" square :ui="{ rounded: 'rounded-full' }">
              <Icon name="mdi:trash-can" />
            </u-button>
          </div>
        </div>
      </div>
      <div class="products-page__card-empty">
        <gh-text class="products-page__card-empty-text">
          Thats all the products that you have.<br />
          You can add more products by clicking the button below.
        </gh-text>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
definePageMeta({
  title: 'Products',
  breadcrumb: [
    {
      label: 'Shop',
    },
    {
      label: 'Products',
      to: '/shop/products'
    }
  ]
})

interface Product {
  id: number
  name: string
  price: number
  stock: number
  image: string
}

const products = ref<Product[]>([
  {
    id: 1,
    name: 'Product 1',
    price: 99.99,
    stock: 10,
    image: 'https://picsum.photos/200',
    isNew: true
  },
  {
    id: 2, 
    name: 'Product 2',
    price: 149.99,
    stock: 5,
    image: 'https://picsum.photos/200',
    isNew: true
  },
  {
    id: 3,
    name: 'Product 3', 
    price: 199.99,
    stock: 15,
    image: 'https://picsum.photos/200'
  },
  {
    id: 4,
    name: 'Product 4',
    price: 249.99,
    stock: 8,
    image: 'https://picsum.photos/200'
  },
  {
    id: 5,
    name: 'Product 5',
    price: 299.99,
    stock: 12,
    image: 'https://picsum.photos/200'
  },
  {
    id: 6,
    name: 'Product 6',
    price: 349.99,
    stock: 7,
    image: 'https://picsum.photos/200'
  },
  {
    id: 7,
    name: 'Product 7',
    price: 399.99,
    stock: 18,
    image: 'https://picsum.photos/200'
  },
  {
    id: 8,
    name: 'Product 8',
    price: 449.99,
    stock: 11,
    image: 'https://picsum.photos/200'
  }
])

const searchQuery = ref('')

const filteredProducts = computed(() => {
  return products.value.filter(product => 
    product.name.toLowerCase().includes(searchQuery.value.toLowerCase())
  )
})
</script>
<style lang="scss" scoped>
.products-page {
  @apply w-full;
  &__header {
    @apply w-full flex flex-col gap-2;
  }
  &__title {
    @apply text-3xl font-semibold text-gray-900;
  }
  &__content {
    @apply w-full mt-4;
  }
  &__grid {
    @apply grid grid-cols-4 gap-4;
    @media (max-width: theme('screens.xl')) {
      @apply grid-cols-3;
    }
    @media (max-width: theme('screens.md')) {
      @apply grid-cols-2;
    }
    @media (max-width: theme('screens.sm')) {
      @apply grid-cols-1;
    }
  }
  &__search {
    @apply w-full flex flex-row items-center gap-2;
  }
  &__card {
    @apply relative bg-white rounded-lg shadow-sm border border-gray-200 overflow-hidden cursor-pointer;
    &:hover {
      @apply shadow-lg;
    }
    &-image {
      @apply w-full aspect-[4/3];
      img {
        @apply w-full h-full object-cover;
      }
    }
    &-body {
      @apply p-4 flex flex-col gap-2;
    }
    &-title {
      @apply text-lg font-semibold text-gray-900;
    }
    &-price {
      @apply text-base text-vermillion-500 font-semibold;
    }
    &-stock {
      @apply text-sm text-gray-500;
    }
    &-content {
      @apply p-4;
    }
    &-badge {
      @apply bg-green-500 text-white text-xs px-2 py-1 rounded-full absolute top-2 right-2;
    }
    &-actions {
      @apply w-full flex flex-row gap-2 justify-end border-t border-gray-200 px-4 py-2;
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
