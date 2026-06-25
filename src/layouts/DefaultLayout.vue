<template>
  <div class="min-h-screen flex flex-col font-sans text-slate-900 selection:bg-blue-100 selection:text-blue-900 overflow-x-hidden">
    <AppNavbar />
    <main class="flex-1 bg-white">
      <RouterView />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
import AppNavbar from '@/components/AppNavbar.vue'
import AppFooter from '@/components/AppFooter.vue'
</script>
