<template>
  <footer class="bg-gray-900 text-gray-300">
    <!-- Main Footer Content -->
    <div class="border-b border-gray-800">
      <UContainer>
        <div class="py-12 lg:py-16">
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
            <!-- Company Info -->
            <div class="space-y-4">
              <div class="flex items-center gap-2">
                <div class="w-10 h-10 rounded-lg bg-brand-500 flex items-center justify-center">
                  <UIcon name="i-heroicons-heart" class="w-6 h-6 text-white" />
                </div>
                <span class="text-xl font-bold text-white">
                  داروخانه آنلاین
                </span>
              </div>
              <p class="text-sm leading-relaxed text-gray-400">
                ارائه‌دهنده معتبر دارو و محصولات بهداشتی با تحویل سریع و ایمن در سراسر کشور.
                سلامتی شما، اولویت ماست.
              </p>
              <!-- Trust Badges -->
              <div class="flex gap-3 pt-2">
                <div class="bg-gray-800 rounded-lg px-3 py-2 text-xs">
                  <UIcon name="i-heroicons-shield-check" class="w-4 h-4 text-green-400 inline-block mb-1" />
                  <span class="mr-1">مجوز رسمی</span>
                </div>
                <div class="bg-gray-800 rounded-lg px-3 py-2 text-xs">
                  <UIcon name="i-heroicons-lock-closed" class="w-4 h-4 text-blue-400 inline-block mb-1" />
                  <span class="mr-1">پرداخت امن</span>
                </div>
              </div>
            </div>

            <!-- Quick Links -->
            <div>
              <h3 class="text-white font-bold text-base mb-4">دسترسی سریع</h3>
              <ul class="space-y-3">
                <li v-for="link in quickLinks" :key="link.path">
                  <NuxtLink
                    :to="link.path"
                    class="text-sm hover:text-brand-400 transition-colors inline-flex items-center gap-2"
                  >
                    <UIcon name="i-heroicons-chevron-left" class="w-3 h-3" />
                    {{ link.label }}
                  </NuxtLink>
                </li>
              </ul>
            </div>

            <!-- Customer Service -->
            <div>
              <h3 class="text-white font-bold text-base mb-4">خدمات مشتریان</h3>
              <ul class="space-y-3">
                <li v-for="link in serviceLinks" :key="link.path">
                  <NuxtLink
                    :to="link.path"
                    class="text-sm hover:text-brand-400 transition-colors inline-flex items-center gap-2"
                  >
                    <UIcon name="i-heroicons-chevron-left" class="w-3 h-3" />
                    {{ link.label }}
                  </NuxtLink>
                </li>
              </ul>
            </div>

            <!-- Contact Info -->
            <div>
              <h3 class="text-white font-bold text-base mb-4">تماس با ما</h3>
              <ul class="space-y-4">
                <li class="flex items-start gap-3">
                  <UIcon name="i-heroicons-phone" class="w-5 h-5 text-brand-400 mt-0.5 flex-shrink-0" />
                  <div class="text-sm">
                    <p class="text-white font-medium">۰۲۱-۱۲۳۴۵۶۷۸</p>
                    <p class="text-xs text-gray-400">۲۴ ساعته، ۷ روز هفته</p>
                  </div>
                </li>
                <li class="flex items-start gap-3">
                  <UIcon name="i-heroicons-envelope" class="w-5 h-5 text-brand-400 mt-0.5 flex-shrink-0" />
                  <div class="text-sm">
                    <p class="text-white">info@pharmacy.ir</p>
                  </div>
                </li>
                <li class="flex items-start gap-3">
                  <UIcon name="i-heroicons-map-pin" class="w-5 h-5 text-brand-400 mt-0.5 flex-shrink-0" />
                  <div class="text-sm">
                    <p class="text-gray-400">تهران، خیابان ولیعصر، پلاک ۱۲۳</p>
                  </div>
                </li>
              </ul>

              <!-- Social Media -->
              <div class="mt-6">
                <p class="text-sm text-gray-400 mb-3">ما را دنبال کنید</p>
                <div class="flex gap-2">
                  <a
                    href="#"
                    class="w-9 h-9 rounded-lg bg-gray-800 hover:bg-brand-500 flex items-center justify-center transition-colors"
                    aria-label="اینستاگرام"
                  >
                    <UIcon name="i-heroicons-camera" class="w-5 h-5" />
                  </a>
                  <a
                    href="#"
                    class="w-9 h-9 rounded-lg bg-gray-800 hover:bg-brand-500 flex items-center justify-center transition-colors"
                    aria-label="تلگرام"
                  >
                    <UIcon name="i-heroicons-paper-airplane" class="w-5 h-5" />
                  </a>
                  <a
                    href="#"
                    class="w-9 h-9 rounded-lg bg-gray-800 hover:bg-brand-500 flex items-center justify-center transition-colors"
                    aria-label="توییتر"
                  >
                    <UIcon name="i-heroicons-at-symbol" class="w-5 h-5" />
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </UContainer>
    </div>

    <!-- Bottom Bar -->
    <div class="bg-gray-950">
      <UContainer>
        <div class="py-6">
          <div class="flex flex-col md:flex-row justify-between items-center gap-4 text-sm text-gray-500">
            <p>© {{ currentYear }} داروخانه آنلاین. تمامی حقوق محفوظ است.</p>
            <div class="flex gap-6">
              <NuxtLink to="/privacy" class="hover:text-brand-400 transition-colors">
                حریم خصوصی
              </NuxtLink>
              <NuxtLink to="/terms" class="hover:text-brand-400 transition-colors">
                قوانین و مقررات
              </NuxtLink>
              <NuxtLink to="/cookies" class="hover:text-brand-400 transition-colors">
                کوکی‌ها
              </NuxtLink>
            </div>
          </div>
        </div>
      </UContainer>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterComponent',

  data() {
    return {
      quickLinks: [
        { label: 'داروها', path: '/medications' },
        { label: 'محصولات بهداشتی', path: '/health-products' },
        { label: 'مکمل‌ها', path: '/supplements' },
        { label: 'ویتامین‌ها', path: '/vitamins' },
        { label: 'درباره ما', path: '/about' }
      ],
      serviceLinks: [
        { label: 'پرسش‌های متداول', path: '/faq' },
        { label: 'راهنمای خرید', path: '/guide' },
        { label: 'رویه ارسال', path: '/shipping' },
        { label: 'رویه بازگشت', path: '/returns' },
        { label: 'پیگیری سفارش', path: '/track-order' }
      ]
    }
  },

  computed: {
    currentYear() {
      return new Date().getFullYear()
    }
  }
}
</script>
