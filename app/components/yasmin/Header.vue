<template>
  <header :class="['fixed top-0 left-0 right-0 z-50 transition-all duration-500', scrolled ? 'bg-white/92 backdrop-blur-xl border-b border-rose-100 shadow-md shadow-rose-50' : 'bg-transparent']">
    <div class="max-w-7xl mx-auto px-6 flex items-center justify-between py-4">

      <!-- Logo -->
      <a href="#inicio" class="flex items-center gap-2.5 group" @click.prevent="scrollTo('inicio')">
        <div class="w-9 h-9 bg-rose-400 rounded-xl flex items-center justify-center shadow-lg shadow-rose-400/30 group-hover:scale-110 transition-transform duration-200">
          <span class="text-white text-base">🍼</span>
        </div>
        <div class="flex flex-col leading-none">
          <span style="font-family: 'Playfair Display', serif;" class="text-lg font-bold text-gray-900 tracking-tight">Yasmim <span class="text-rose-400">& Hércules</span></span>
          <span class="text-[10px] text-gray-400 uppercase tracking-widest">Fotografia</span>
        </div>
      </a>

      <!-- Nav desktop -->
      <nav class="hidden md:flex items-center gap-1">
        <a v-for="item in navItems" :key="item.id" :href="`#${item.id}`"
          :class="['relative px-4 py-2 text-sm font-medium rounded-lg transition-all duration-200', activeSection === item.id ? 'text-rose-500 bg-rose-50' : 'text-gray-500 hover:text-gray-900 hover:bg-gray-100']"
          @click.prevent="scrollTo(item.id)">
          {{ item.label }}
          <span v-if="activeSection === item.id" class="absolute bottom-1 left-1/2 -translate-x-1/2 w-1 h-1 bg-rose-400 rounded-full" />
        </a>
      </nav>

      <!-- CTAs -->
      <div class="hidden md:flex items-center gap-3">
        <a href="https://wa.me/5561982514499" target="_blank"
          class="inline-flex items-center gap-2 bg-rose-500 hover:bg-rose-400 text-white font-semibold px-5 py-2.5 rounded-xl transition-all duration-200 hover:scale-105 text-sm shadow-lg shadow-rose-500/20">
          💬 Agendar
        </a>
      </div>

      <!-- Hambúrguer mobile -->
      <button class="md:hidden flex flex-col gap-1.5 p-2 rounded-lg hover:bg-rose-50 transition-colors" @click="mobileOpen = !mobileOpen">
        <span :class="['block w-5 h-0.5 bg-gray-800 transition-all duration-300', mobileOpen ? 'rotate-45 translate-y-2' : '']" />
        <span :class="['block w-5 h-0.5 bg-gray-800 transition-all duration-300', mobileOpen ? 'opacity-0' : '']" />
        <span :class="['block w-5 h-0.5 bg-gray-800 transition-all duration-300', mobileOpen ? '-rotate-45 -translate-y-2' : '']" />
      </button>
    </div>

    <!-- Mobile menu -->
    <Transition enter-active-class="transition-all duration-300 ease-out" enter-from-class="opacity-0 -translate-y-2" enter-to-class="opacity-100 translate-y-0" leave-active-class="transition-all duration-200" leave-from-class="opacity-100 translate-y-0" leave-to-class="opacity-0 -translate-y-2">
      <div v-if="mobileOpen" class="md:hidden bg-white/95 backdrop-blur-xl border-t border-rose-100 px-6 pb-6 pt-4">
        <nav class="flex flex-col gap-1 mb-5">
          <a v-for="item in navItems" :key="item.id"
            :class="['px-4 py-3 text-sm font-medium rounded-xl transition-all duration-200', activeSection === item.id ? 'text-rose-500 bg-rose-50' : 'text-gray-500 hover:text-gray-900 hover:bg-gray-50']"
            @click.prevent="scrollTo(item.id); mobileOpen = false">{{ item.label }}</a>
        </nav>
        <a href="https://wa.me/5561982514499" target="_blank" class="flex items-center justify-center gap-2 bg-rose-500 text-white font-semibold py-3 rounded-xl">
          💬 Agendar pelo WhatsApp
        </a>
      </div>
    </Transition>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'
const navItems = [
  { id: 'inicio', label: 'Início' }, { id: 'sobre', label: 'Sobre' },
  { id: 'portfolio', label: 'Portfólio' }, { id: 'contato', label: 'Contato' },
]
const scrolled = ref(false); const mobileOpen = ref(false); const activeSection = ref('inicio')
function onScroll() {
  scrolled.value = window.scrollY > 20
  for (const item of [...navItems].reverse()) { const el = document.getElementById(item.id); if (el && window.scrollY >= el.offsetTop - 120) { activeSection.value = item.id; break } }
}
function scrollTo(id: string) { document.getElementById(id)?.scrollIntoView({ behavior: 'smooth', block: 'start' }) }
onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>
