<template>
  <div class="accounting-page">
    <div class="accounting-page__content">
      <div class="accounting-page__grid">
        <!-- Revenue Overview Card -->
        <div class="accounting-page__card">
          <div class="accounting-page__card-header">
            <gh-text class="accounting-page__card-title">Revenue Overview</gh-text>
          </div>
          <div class="accounting-page__card-content">
            <div class="accounting-page__card-stat">
              <gh-text class="accounting-page__card-value">$45,678</gh-text>
              <gh-text class="accounting-page__card-label">Total Revenue</gh-text>
            </div>
            <div class="accounting-page__card-stat">
              <gh-text class="accounting-page__card-value">+23%</gh-text>
              <gh-text class="accounting-page__card-label">vs Last Month</gh-text>
            </div>
          </div>
        </div>

        <!-- Expenses Card -->
        <div class="accounting-page__card">
          <div class="accounting-page__card-header">
            <gh-text class="accounting-page__card-title">Expenses</gh-text>
          </div>
          <div class="accounting-page__card-content">
            <div class="accounting-page__card-stat">
              <gh-text class="accounting-page__card-value">$12,345</gh-text>
              <gh-text class="accounting-page__card-label">Total Expenses</gh-text>
            </div>
            <div class="accounting-page__card-stat">
              <gh-text class="accounting-page__card-value">-8%</gh-text>
              <gh-text class="accounting-page__card-label">vs Last Month</gh-text>
            </div>
          </div>
        </div>

        <!-- Profit Margins Card -->
        <div class="accounting-page__card">
          <div class="accounting-page__card-header">
            <gh-text class="accounting-page__card-title">Profit Margins</gh-text>
          </div>
          <div class="accounting-page__card-content">
            <div class="accounting-page__card-stat">
              <gh-text class="accounting-page__card-value">32%</gh-text>
              <gh-text class="accounting-page__card-label">Gross Margin</gh-text>
            </div>
            <div class="accounting-page__card-stat">
              <gh-text class="accounting-page__card-value">18%</gh-text>
              <gh-text class="accounting-page__card-label">Net Margin</gh-text>
            </div>
          </div>
        </div>

        <!-- Cash Flow Card -->
        <div class="accounting-page__card">
          <div class="accounting-page__card-header">
            <gh-text class="accounting-page__card-title">Cash Flow</gh-text>
          </div>
          <div class="accounting-page__card-content">
            <div class="accounting-page__card-stat">
              <gh-text class="accounting-page__card-value">$28,456</gh-text>
              <gh-text class="accounting-page__card-label">Operating Cash Flow</gh-text>
            </div>
            <div class="accounting-page__card-stat">
              <gh-text class="accounting-page__card-value">$15,789</gh-text>
              <gh-text class="accounting-page__card-label">Free Cash Flow</gh-text>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
definePageMeta({
  title: 'Accounting',
  breadcrumb: [
    {
      label: 'Shop',
    },
    {
      label: 'Accounting',
      to: '/shop/accounting'
    }
  ]
})
</script>

<style lang="scss" scoped>
.accounting-page {
  @apply w-full;
  &__header {
    @apply w-full flex flex-col gap-2;
  }
  &__title {
    @apply text-3xl font-semibold text-gray-900;
  }
  &__content {
    @apply w-full;
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
  &__card {
    @apply bg-white rounded-lg shadow-sm border border-gray-200 overflow-hidden;
    &:hover {
      @apply shadow-lg;
    }
    &-header {
      @apply flex flex-row items-center justify-between p-4 border-b border-gray-200;
    }
    &-title {
      @apply text-lg font-semibold text-gray-900;
    }
    &-content {
      @apply p-4 flex flex-col gap-3;
    }
    &-stat {
      @apply flex flex-col gap-1;
    }
    &-value {
      @apply text-2xl font-semibold text-gray-900;
    }
    &-label {
      @apply text-sm text-gray-500;
    }
  }
}
</style>
