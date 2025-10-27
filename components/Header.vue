<template>
  <header class="sticky top-0 z-50 bg-white dark:bg-gray-900 border-b border-gray-200 dark:border-gray-800 transition-colors duration-300">
    <div class="max-w-7xl mx-auto px-4 lg:px-8">
      <div class="flex items-center justify-between h-16 lg:h-20 gap-4">

        <!-- Logo -->
        <NuxtLink to="/" class="flex items-center gap-3 flex-shrink-0">
          <div class="w-10 h-10 flex items-center justify-center">
            <svg width="40" height="40" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
              <circle cx="16" cy="16" r="16" :fill="colorMode.value === 'dark' ? '#14B8A6' : '#2C7A7B'"/>
              <circle cx="16" cy="16" r="8" fill="white"/>
            </svg>
          </div>
          <span class="text-xl lg:text-2xl font-black text-gray-900 dark:text-white">دارو پلاس</span>
        </NuxtLink>

        <!-- Desktop Navigation -->
        <nav class="hidden md:flex items-center gap-6 lg:gap-8 flex-1 justify-center">
          <NuxtLink
              to="/"
              class="text-sm lg:text-base font-semibold text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 transition-colors"
          >
            صفحه اصلی
          </NuxtLink>
          <NuxtLink
              to="/medications"
              class="text-sm lg:text-base font-semibold text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 transition-colors"
          >
            داروها
          </NuxtLink>
          <NuxtLink
              to="/products"
              class="text-sm lg:text-base font-semibold text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 transition-colors"
          >
            محصولات سلامت
          </NuxtLink>
          <NuxtLink
              to="/wellness"
              class="text-sm lg:text-base font-semibold text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 transition-colors"
          >
            سلامت و تندرستی
          </NuxtLink>
          <NuxtLink
              to="/about"
              class="text-sm lg:text-base font-semibold text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 transition-colors"
          >
            درباره ما
          </NuxtLink>
        </nav>

        <!-- Actions -->
        <div class="flex items-center gap-2">
          <!-- Messages -->
          <button
              class="relative p-2 rounded-lg text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 hover:bg-teal-50 dark:hover:bg-teal-950 transition-all"
              aria-label="پیام‌ها"
          >
            <UIcon name="i-heroicons-chat-bubble-left-right" class="w-6 h-6" />
            <span
                v-if="unreadMessages > 0"
                class="absolute -top-1 -left-1 bg-red-500 text-white text-xs font-bold px-1.5 py-0.5 rounded-full min-w-[18px] text-center"
            >
              {{ unreadMessages }}
            </span>
          </button>

          <!-- Search -->
          <button
              class="p-2 rounded-lg text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 hover:bg-teal-50 dark:hover:bg-teal-950 transition-all"
              aria-label="جستجو"
          >
            <UIcon name="i-heroicons-magnifying-glass" class="w-6 h-6" />
          </button>

          <!-- Cart -->
          <NuxtLink
              to="/cart"
              class="relative p-2 rounded-lg text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 hover:bg-teal-50 dark:hover:bg-teal-950 transition-all"
              aria-label="سبد خرید"
          >
            <UIcon name="i-heroicons-shopping-cart" class="w-6 h-6" />
            <span
                v-if="cartItemsCount > 0"
                class="absolute -top-1 -left-1 bg-red-500 text-white text-xs font-bold px-1.5 py-0.5 rounded-full min-w-[18px] text-center"
            >
              {{ cartItemsCount }}
            </span>
          </NuxtLink>

          <!-- Dark Mode Toggle -->
          <button
              class="p-2 rounded-lg text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 hover:bg-teal-50 dark:hover:bg-teal-950 transition-all"
              aria-label="تغییر تم"
              @click="toggleDarkMode"
          >
            <UIcon :name="colorMode.value === 'dark' ? 'i-heroicons-sun' : 'i-heroicons-moon'" class="w-6 h-6" />
          </button>

          <!-- User Profile -->
          <button
              class="hidden sm:flex p-2 rounded-lg text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 hover:bg-teal-50 dark:hover:bg-teal-950 transition-all"
              aria-label="پروفایل کاربر"
          >
            <UIcon name="i-heroicons-user" class="w-6 h-6" />
          </button>

          <!-- Mobile Menu Toggle -->
          <button
              class="md:hidden p-2 rounded-lg text-gray-600 dark:text-gray-300 hover:text-teal-500 dark:hover:text-teal-400 hover:bg-teal-50 dark:hover:bg-teal-950 transition-all"
              aria-label="منو"
              @click="toggleMobileMenu"
          >
            <UIcon name="i-heroicons-bars-3" class="w-6 h-6" />
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Menu -->
    <Transition
        enter-active-class="transition-all duration-300 ease-out"
        enter-from-class="opacity-0 translate-x-full"
        enter-to-class="opacity-100 translate-x-0"
        leave-active-class="transition-all duration-300 ease-in"
        leave-from-class="opacity-100 translate-x-0"
        leave-to-class="opacity-0 translate-x-full"
    >
      <div
          v-if="mobileMenuOpen"
          class="fixed inset-0 z-50 md:hidden"
          @click="closeMobileMenu"
      >
        <!-- Backdrop -->
        <div class="absolute inset-0 bg-black/50"/>

        <!-- Menu Panel -->
        <div
            class="absolute top-0 right-0 w-80 max-w-[85vw] h-full bg-white dark:bg-gray-900 shadow-2xl"
            @click.stop
        >
          <!-- Menu Header -->
          <div class="flex items-center justify-between p-6 border-b border-gray-200 dark:border-gray-800">
            <div class="flex items-center gap-3">
              <div class="w-8 h-8 flex items-center justify-center">
                <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <circle cx="16" cy="16" r="16" :fill="colorMode.value === 'dark' ? '#14B8A6' : '#2C7A7B'"/>
                  <circle cx="16" cy="16" r="8" fill="white"/>
                </svg>
              </div>
              <span class="text-lg font-black text-gray-900 dark:text-white">دارو پلاس</span>
            </div>
            <button
                class="p-2 rounded-lg text-gray-500 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white hover:bg-gray-100 dark:hover:bg-gray-800 transition-all"
                @click="closeMobileMenu"
            >
              <UIcon name="i-heroicons-x-mark" class="w-6 h-6" />
            </button>
          </div>

          <!-- Menu Items -->
          <nav class="p-4 space-y-2">
            <NuxtLink
                to="/"
                class="flex items-center gap-3 px-4 py-3 rounded-xl text-gray-900 dark:text-gray-100 hover:bg-teal-50 dark:hover:bg-teal-950 hover:text-teal-600 dark:hover:text-teal-400 transition-all"
                @click="closeMobileMenu"
            >
              <UIcon name="i-heroicons-home" class="w-5 h-5" />
              <span class="font-semibold">صفحه اصلی</span>
            </NuxtLink>
            <NuxtLink
                to="/medications"
                class="flex items-center gap-3 px-4 py-3 rounded-xl text-gray-900 dark:text-gray-100 hover:bg-teal-50 dark:hover:bg-teal-950 hover:text-teal-600 dark:hover:text-teal-400 transition-all"
                @click="closeMobileMenu"
            >
              <UIcon name="i-heroicons-beaker" class="w-5 h-5" />
              <span class="font-semibold">داروها</span>
            </NuxtLink>
            <NuxtLink
                to="/products"
                class="flex items-center gap-3 px-4 py-3 rounded-xl text-gray-900 dark:text-gray-100 hover:bg-teal-50 dark:hover:bg-teal-950 hover:text-teal-600 dark:hover:text-teal-400 transition-all"
                @click="closeMobileMenu"
            >
              <UIcon name="i-heroicons-heart" class="w-5 h-5" />
              <span class="font-semibold">محصولات سلامت</span>
            </NuxtLink>
            <NuxtLink
                to="/wellness"
                class="flex items-center gap-3 px-4 py-3 rounded-xl text-gray-900 dark:text-gray-100 hover:bg-teal-50 dark:hover:bg-teal-950 hover:text-teal-600 dark:hover:text-teal-400 transition-all"
                @click="closeMobileMenu"
            >
              <UIcon name="i-heroicons-sparkles" class="w-5 h-5" />
              <span class="font-semibold">سلامت و تندرستی</span>
            </NuxtLink>
            <NuxtLink
                to="/about"
                class="flex items-center gap-3 px-4 py-3 rounded-xl text-gray-900 dark:text-gray-100 hover:bg-teal-50 dark:hover:bg-teal-950 hover:text-teal-600 dark:hover:text-teal-400 transition-all"
                @click="closeMobileMenu"
            >
              <UIcon name="i-heroicons-information-circle" class="w-5 h-5" />
              <span class="font-semibold">درباره ما</span>
            </NuxtLink>
          </nav>
        </div>
      </div>
    </Transition>
  </header>
</template>

<script setup lang="ts">
import { useCartStore } from '~/stores/cart'

const colorMode = useColorMode()
const cartStore = useCartStore()

const mobileMenuOpen = ref(false)
const unreadMessages = ref(1)

const cartItemsCount = computed(() => cartStore.totalItems)

const toggleDarkMode = () => {
  colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
}

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
  if (mobileMenuOpen.value) {
    document.body.style.overflow = 'hidden'
  } else {
    document.body.style.overflow = ''
  }
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
  document.body.style.overflow = ''
}

onUnmounted(() => {
  document.body.style.overflow = ''
})
</script>