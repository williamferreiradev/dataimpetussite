<template>
  <div>
    <!-- ── FILTROS ── -->
    <div class="flex flex-wrap justify-center gap-2 mb-12">
      <button
        v-for="cat in categories"
        :key="cat"
        :class="[
          'px-5 py-2 rounded-full text-sm font-medium transition-all duration-200',
          activeFilter === cat
            ? 'bg-brand-500 text-white shadow-warm-sm scale-105'
            : 'bg-white text-stone-500 border border-stone-200 hover:border-brand-300 hover:text-brand-600 shadow-card'
        ]"
        @click="setFilter(cat)"
      >
        {{ cat }}
      </button>
    </div>

    <!-- ── GRID MASONRY ── -->
    <div class="columns-1 sm:columns-2 lg:columns-3 gap-4 space-y-4">
      <div
        v-for="(photo, i) in filteredPhotos"
        :key="photo.id"
        class="break-inside-avoid group relative overflow-hidden rounded-2xl cursor-pointer shadow-card hover:shadow-card-hover transition-all duration-500 hover:-translate-y-1"
        @click="openLightbox(i)"
      >
        <img
          :src="photo.src"
          :alt="photo.title"
          :class="['w-full object-cover transition-transform duration-700 group-hover:scale-105', photo.tall ? 'aspect-[3/4]' : 'aspect-[4/3]']"
          loading="lazy"
        />

        <!-- Overlay hover -->
        <div class="absolute inset-0 bg-gradient-to-t from-stone-900/80 via-stone-900/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-400 flex flex-col justify-end p-5">
          <div class="translate-y-4 group-hover:translate-y-0 transition-transform duration-400">
            <span class="inline-block text-xs font-semibold uppercase tracking-widest text-brand-300 mb-1">
              {{ photo.category }}
            </span>
            <h3 class="text-white font-serif text-xl font-semibold leading-tight">{{ photo.title }}</h3>
            <p class="text-stone-300 text-sm mt-1">{{ photo.subtitle }}</p>
          </div>
          <!-- Ícone de expandir -->
          <div class="absolute top-4 right-4 w-9 h-9 bg-white/20 backdrop-blur-sm rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transition-all duration-300">
            <svg class="w-4 h-4 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M4 8V4m0 0h4M4 4l5 5m11-1V4m0 0h-4m4 0l-5 5M4 16v4m0 0h4m-4 0l5-5m11 5l-5-5m5 5v-4m0 4h-4" />
            </svg>
          </div>
        </div>
      </div>
    </div>

    <!-- ── LIGHTBOX ── -->
    <Teleport to="body">
      <Transition
        enter-active-class="transition-all duration-300 ease-out"
        enter-from-class="opacity-0"
        enter-to-class="opacity-100"
        leave-active-class="transition-all duration-200 ease-in"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
      >
        <div
          v-if="lightboxOpen"
          class="fixed inset-0 z-[100] bg-stone-950/95 backdrop-blur-xl flex items-center justify-center p-4"
          @click.self="closeLightbox"
          @keydown.esc="closeLightbox"
          tabindex="-1"
          ref="lightboxEl"
        >
          <!-- Fechar -->
          <button
            class="absolute top-5 right-5 w-11 h-11 rounded-full bg-white/10 hover:bg-white/20 text-white flex items-center justify-center transition-colors z-10"
            @click="closeLightbox"
          >
            <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>

          <!-- Nav anterior -->
          <button
            class="absolute left-4 top-1/2 -translate-y-1/2 w-12 h-12 rounded-full bg-white/10 hover:bg-white/20 text-white flex items-center justify-center transition-all hover:scale-110 z-10"
            @click="prevPhoto"
          >
            <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
            </svg>
          </button>

          <!-- Imagem principal -->
          <Transition
            enter-active-class="transition-all duration-300"
            enter-from-class="opacity-0 scale-95"
            enter-to-class="opacity-100 scale-100"
            leave-active-class="transition-all duration-200"
            leave-from-class="opacity-100 scale-100"
            leave-to-class="opacity-0 scale-95"
            mode="out-in"
          >
            <div :key="currentIndex" class="flex flex-col items-center gap-5 max-w-4xl w-full">
              <img
                :src="filteredPhotos[currentIndex]?.src"
                :alt="filteredPhotos[currentIndex]?.title"
                class="max-h-[75vh] max-w-full object-contain rounded-2xl shadow-warm-lg"
              />
              <!-- Info -->
              <div class="text-center">
                <span class="text-brand-400 text-xs font-semibold uppercase tracking-widest">
                  {{ filteredPhotos[currentIndex]?.category }}
                </span>
                <h3 class="text-white font-serif text-2xl font-semibold mt-1">
                  {{ filteredPhotos[currentIndex]?.title }}
                </h3>
                <p class="text-stone-400 text-sm mt-1">{{ filteredPhotos[currentIndex]?.subtitle }}</p>
              </div>
              <!-- Contador -->
              <p class="text-stone-600 text-xs">{{ currentIndex + 1 }} / {{ filteredPhotos.length }}</p>
            </div>
          </Transition>

          <!-- Nav próximo -->
          <button
            class="absolute right-4 top-1/2 -translate-y-1/2 w-12 h-12 rounded-full bg-white/10 hover:bg-white/20 text-white flex items-center justify-center transition-all hover:scale-110 z-10"
            @click="nextPhoto"
          >
            <svg class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7" />
            </svg>
          </button>

          <!-- Thumbnails -->
          <div class="absolute bottom-5 left-1/2 -translate-x-1/2 flex gap-2">
            <button
              v-for="(photo, i) in filteredPhotos"
              :key="photo.id"
              :class="[
                'w-2 h-2 rounded-full transition-all duration-200',
                i === currentIndex ? 'bg-brand-400 scale-125' : 'bg-white/30 hover:bg-white/60'
              ]"
              @click="currentIndex = i"
            />
          </div>
        </div>
      </Transition>
    </Teleport>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted, nextTick } from 'vue'

interface Photo {
  id:       number
  src:      string
  title:    string
  subtitle: string
  category: string
  tall:     boolean
}

const photos: Photo[] = [
  { id: 1, src: '/p1.png', title: 'O Grande Dia',       subtitle: 'Cerimônia religiosa · São Paulo',  category: 'Casamento',  tall: true  },
  { id: 2, src: '/p2.png', title: 'Amor ao Pôr do Sol', subtitle: 'Ensaio externo · Campos do Jordão', category: 'Ensaio',     tall: false },
  { id: 3, src: '/p3.png', title: 'Detalhes que Marcam',subtitle: 'Buquê · Casamento civil',           category: 'Detalhes',   tall: false },
  { id: 4, src: '/p4.png', title: 'Nossa Dança',         subtitle: 'Recepção · Festa de casamento',    category: 'Casamento',  tall: true  },
  { id: 5, src: '/p5.png', title: 'Noiva',               subtitle: 'Portrait · Studio light',          category: 'Portrait',   tall: true  },
  { id: 6, src: '/p6.png', title: 'Juntos para Sempre',  subtitle: 'Pré-wedding · Campo florido',      category: 'Ensaio',     tall: false },
]

const categories  = ['Todos', 'Casamento', 'Ensaio', 'Portrait', 'Detalhes']
const activeFilter = ref('Todos')
const lightboxOpen = ref(false)
const currentIndex = ref(0)
const lightboxEl   = ref<HTMLElement | null>(null)

const filteredPhotos = computed(() =>
  activeFilter.value === 'Todos'
    ? photos
    : photos.filter(p => p.category === activeFilter.value)
)

function setFilter(cat: string) {
  activeFilter.value = cat
  lightboxOpen.value = false
}

async function openLightbox(index: number) {
  currentIndex.value = index
  lightboxOpen.value = true
  await nextTick()
  lightboxEl.value?.focus()
}

function closeLightbox() { lightboxOpen.value = false }

function nextPhoto() {
  currentIndex.value = (currentIndex.value + 1) % filteredPhotos.value.length
}

function prevPhoto() {
  currentIndex.value = (currentIndex.value - 1 + filteredPhotos.value.length) % filteredPhotos.value.length
}

function onKeydown(e: KeyboardEvent) {
  if (!lightboxOpen.value) return
  if (e.key === 'ArrowRight') nextPhoto()
  if (e.key === 'ArrowLeft')  prevPhoto()
  if (e.key === 'Escape')     closeLightbox()
}

onMounted(() => window.addEventListener('keydown', onKeydown))
onUnmounted(() => window.removeEventListener('keydown', onKeydown))
</script>
