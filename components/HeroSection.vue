<template>
  <section class="py-16 lg:py-24">
    <div class="grid lg:grid-cols-2 gap-12 lg:gap-16 items-center">
      <!-- Text Content -->
      <div class="space-y-8 order-2 lg:order-1">
        <!-- AI Badge -->
        <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-brand-50 dark:bg-brand-900/20 text-sm">
          <UIcon name="i-heroicons-sparkles" class="text-brand-500 w-5 h-5" />
          <span class="text-brand-700 dark:text-brand-300 font-medium">دستیار هوشمند آنلاین</span>
        </div>

        <!-- Main Heading -->
        <div>
          <h1 class="text-4xl md:text-5xl lg:text-6xl xl:text-7xl font-black text-gray-900 dark:text-white leading-tight">
            سلامتی شما،
            <span class="text-brand-500 block mt-2">در درب منزل</span>
          </h1>
        </div>

        <!-- Description -->
        <p class="text-lg md:text-xl text-gray-600 dark:text-gray-300 leading-relaxed max-w-2xl">
          دارو و محصولات بهداشتی خود را با تحویل ایمن در منزل دریافت کنید. داروسازان مجرب ۲۴/۷ با پشتیبانی هوش مصنوعی در خدمت شما هستند.
        </p>

        <!-- Features List -->
        <div class="flex flex-wrap gap-6 text-base">
          <div class="flex items-center gap-2">
            <UIcon name="i-heroicons-check-circle" class="text-brand-500 w-6 h-6" />
            <span class="font-medium">تایید سازمان غذا و دارو</span>
          </div>
          <div class="flex items-center gap-2">
            <UIcon name="i-heroicons-check-circle" class="text-brand-500 w-6 h-6" />
            <span class="font-medium">پشتیبانی ۲۴ ساعته</span>
          </div>
          <div class="flex items-center gap-2">
            <UIcon name="i-heroicons-check-circle" class="text-brand-500 w-6 h-6" />
            <span class="font-medium">ارسال رایگان</span>
          </div>
        </div>

        <!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 pt-4">
          <UButton
            size="xl"
            color="primary"
            icon="i-heroicons-shopping-bag"
            to="/medications"
            class="justify-center"
          >
            مشاهده داروها
          </UButton>
          <UButton
            size="xl"
            color="white"
            variant="outline"
            icon="i-heroicons-chat-bubble-left-right"
            class="justify-center"
            @click="openChat"
          >
            گفتگو با دستیار هوشمند
          </UButton>
        </div>
      </div>

      <!-- Image/Illustration -->
      <div class="order-1 lg:order-2">
        <div class="aspect-square rounded-3xl bg-gradient-to-br from-brand-100 via-brand-200 to-brand-300 dark:from-brand-900 dark:to-brand-800 flex items-center justify-center relative overflow-hidden shadow-2xl">
          <!-- Decorative elements -->
          <div class="absolute inset-0 bg-white/5 backdrop-blur-3xl"></div>
          <div class="absolute top-10 right-10 w-32 h-32 bg-white/10 rounded-full blur-2xl"></div>
          <div class="absolute bottom-10 left-10 w-40 h-40 bg-brand-400/20 rounded-full blur-3xl"></div>
          
          <!-- Icon -->
          <UIcon name="i-heroicons-building-storefront" class="w-48 h-48 text-brand-500 opacity-30 relative z-10" />
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { useChatStore } from '~/stores/chat'

export default defineComponent({
  name: 'HeroSection',

  methods: {
    openChat() {
      const chatStore = useChatStore()
      chatStore.toggleChat()
    }
  }
})
</script>
