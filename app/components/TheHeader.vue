<template>
  <header
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-500',
      scrolled
        ? 'bg-stone-50/90 backdrop-blur-xl border-b border-stone-200/80 shadow-card'
        : 'bg-transparent'
    ]"
  >
    <div class="max-w-7xl mx-auto px-6 flex items-center justify-between py-4">

      <!-- Logo -->
      <a href="#inicio" class="flex items-center gap-2.5 group" @click.prevent="scrollTo('inicio')">
        <div class="w-9 h-9 bg-brand-500 rounded-xl flex items-center justify-center shadow-warm-sm group-hover:scale-110 transition-transform duration-200">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
            <path stroke-linecap="round" stroke-linejoin="round" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z" />
            <path stroke-linecap="round" stroke-linejoin="round" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z" />
          </svg>
        </div>
        <div class="flex flex-col leading-none">
          <span class="font-serif text-lg font-bold text-stone-900 tracking-tight">Emilly <span class="text-brand-500">& Pedro</span></span>
          <span class="text-[10px] font-sans text-stone-400 uppercase tracking-widest">Fotografia</span>
        </div>
      </a>

      <!-- Nav desktop -->
      <nav class="hidden md:flex items-center gap-1">
        <a
          v-for="item in navItems"
          :key="item.id"
          :href="`#${item.id}`"
          :class="[
            'relative px-4 py-2 font-sans text-sm font-medium rounded-lg transition-all duration-200',
            activeSection === item.id
              ? 'text-brand-600 bg-brand-50'
              : 'text-stone-500 hover:text-stone-900 hover:bg-stone-100'
          ]"
          @click.prevent="scrollTo(item.id)"
        >
          {{ item.label }}
          <span
            v-if="activeSection === item.id"
            class="absolute bottom-1 left-1/2 -translate-x-1/2 w-1 h-1 bg-brand-500 rounded-full"
          />
        </a>
      </nav>

      <!-- CTAs -->
      <div class="hidden md:flex items-center gap-3">
        <BaseButton variant="ghost" size="sm" @click="scrollTo('contato')">Contato</BaseButton>
        <BaseButton variant="primary" size="sm" @click="scrollTo('portfolio')">
          Ver portfólio
        </BaseButton>
      </div>

      <!-- Hambúrguer mobile -->
      <button
        class="md:hidden flex flex-col gap-1.5 p-2 rounded-lg hover:bg-stone-100 transition-colors"
        @click="mobileOpen = !mobileOpen"
      >
        <span :class="['block w-5 h-0.5 bg-stone-800 transition-all duration-300', mobileOpen ? 'rotate-45 translate-y-2' : '']" />
        <span :class="['block w-5 h-0.5 bg-stone-800 transition-all duration-300', mobileOpen ? 'opacity-0' : '']" />
        <span :class="['block w-5 h-0.5 bg-stone-800 transition-all duration-300', mobileOpen ? '-rotate-45 -translate-y-2' : '']" />
      </button>
    </div>

    <!-- Mobile menu -->
    <Transition
      enter-active-class="transition-all duration-300 ease-out"
      enter-from-class="opacity-0 -translate-y-2"
      enter-to-class="opacity-100 translate-y-0"
      leave-active-class="transition-all duration-200 ease-in"
      leave-from-class="opacity-100 translate-y-0"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div v-if="mobileOpen" class="md:hidden bg-stone-50/97 backdrop-blur-xl border-t border-stone-200 px-6 pb-6 pt-4">
        <nav class="flex flex-col gap-1 mb-5">
          <a
            v-for="item in navItems"
            :key="item.id"
            :class="[
              'px-4 py-3 text-sm font-medium rounded-xl transition-all duration-200',
              activeSection === item.id
                ? 'text-brand-600 bg-brand-50'
                : 'text-stone-500 hover:text-stone-900 hover:bg-stone-100'
            ]"
            @click.prevent="scrollTo(item.id); mobileOpen = false"
          >{{ item.label }}</a>
        </nav>
        <BaseButton variant="primary" size="md" :full="true" @click="scrollTo('contato'); mobileOpen = false">
          Fale comigo
        </BaseButton>
      </div>
    </Transition>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const navItems = [
  { id: 'inicio',    label: 'Início'    },
  { id: 'sobre',     label: 'Sobre'     },
  { id: 'portfolio', label: 'Portfólio' },
  { id: 'contato',   label: 'Contato'   },
]

const scrolled      = ref(false)
const mobileOpen    = ref(false)
const activeSection = ref('inicio')

function onScroll() {
  scrolled.value = window.scrollY > 20
  for (const item of [...navItems].reverse()) {
    const el = document.getElementById(item.id)
    if (el && window.scrollY >= el.offsetTop - 120) {
      activeSection.value = item.id
      break
    }
  }
}

function scrollTo(id: string) {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth', block: 'start' })
}

onMounted(() => window.addEventListener('scroll', onScroll, { passive: true }))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>
