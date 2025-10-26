<template>
  <header class="sticky top-0 z-50 bg-white dark:bg-gray-900 border-b border-gray-200 dark:border-gray-800">
    <UContainer>
      <nav class="flex items-center justify-between py-4">
        <!-- Logo -->
        <NuxtLink to="/" class="flex items-center gap-2">
          <div class="w-10 h-10 rounded-lg bg-brand-500 flex items-center justify-center">
            <UIcon name="i-heroicons-heart" class="w-6 h-6 text-white" />
          </div>
          <span class="text-xl font-bold text-gray-900 dark:text-white">
            داروخانه آنلاین
          </span>
        </NuxtLink>

        <!-- Desktop Navigation -->
        <div class="hidden lg:flex items-center gap-8">
          <NuxtLink
            v-for="item in navItems"
            :key="item.path"
            :to="item.path"
            class="relative text-gray-600 dark:text-gray-300 hover:text-brand-500 dark:hover:text-brand-400 transition-colors font-medium text-base"
          >
            {{ item.label }}
          </NuxtLink>
        </div>

        <!-- Actions -->
        <div class="flex items-center gap-3">
          <!-- Search - Desktop -->
          <UButton
            color="white"
            variant="ghost"
            icon="i-heroicons-magnifying-glass"
            square
            size="lg"
            aria-label="جستجو"
            class="hidden md:flex"
            @click="openSearch"
          />

          <!-- Cart -->
          <UButton
            color="white"
            variant="ghost"
            square
            size="lg"
            aria-label="سبد خرید"
            to="/cart"
          >
            <div class="relative">
              <UIcon name="i-heroicons-shopping-cart" class="w-6 h-6" />
              <span
                v-if="cartCount > 0"
                class="absolute -top-2 -left-2 w-5 h-5 bg-brand-500 text-white text-xs rounded-full flex items-center justify-center font-bold"
              >
                {{ cartCount }}
              </span>
            </div>
          </UButton>

          <!-- User Account - Desktop -->
          <UButton
            color="white"
            variant="ghost"
            icon="i-heroicons-user"
            square
            size="lg"
            class="hidden md:flex"
            aria-label="حساب کاربری"
            to="/account"
          />

          <!-- Mobile Menu -->
          <UButton
            color="white"
            variant="ghost"
            icon="i-heroicons-bars-3"
            square
            size="lg"
            class="lg:hidden"
            aria-label="منو"
            @click="mobileMenuOpen = true"
          />
        </div>
      </nav>
    </UContainer>

    <!-- Mobile Menu Drawer -->
    <USlideover v-model="mobileMenuOpen" side="left">
      <div class="p-6 space-y-6">
        <div class="flex items-center justify-between">
          <span class="text-xl font-bold text-gray-900 dark:text-white">منوی اصلی</span>
          <UButton
            color="white"
            variant="ghost"
            icon="i-heroicons-x-mark"
            square
            @click="mobileMenuOpen = false"
          />
        </div>

        <nav class="space-y-4">
          <NuxtLink
            v-for="item in navItems"
            :key="item.path"
            :to="item.path"
            class="block text-lg text-gray-700 dark:text-gray-300 hover:text-brand-500 dark:hover:text-brand-400 transition-colors py-2"
            @click="mobileMenuOpen = false"
          >
            {{ item.label }}
          </NuxtLink>
        </nav>

        <div class="pt-4 border-t border-gray-200 dark:border-gray-800">
          <NuxtLink
            to="/account"
            class="flex items-center gap-3 text-gray-700 dark:text-gray-300 hover:text-brand-500 py-2"
            @click="mobileMenuOpen = false"
          >
            <UIcon name="i-heroicons-user" class="w-5 h-5" />
            <span>حساب کاربری</span>
          </NuxtLink>
        </div>
      </div>
    </USlideover>
  </header>
</template>

<script>
import { useCartStore } from '~/stores/cart'

export default {
  name: 'HeaderComponent',

  data() {
    return {
      mobileMenuOpen: false,
      navItems: [
        { label: 'داروها', path: '/medications' },
        { label: 'محصولات بهداشتی', path: '/health-products' },
        { label: 'مکمل‌ها', path: '/supplements' },
        { label: 'درباره ما', path: '/about' }
      ]
    }
  },

  computed: {
    cartStore() {
      return useCartStore()
    },

    cartCount() {
      return this.cartStore.itemCount
    }
  },

  methods: {
    openSearch() {
      console.log('Open search')
    }
  }
}
</script>
