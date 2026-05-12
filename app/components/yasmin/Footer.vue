<template>
  <footer class="bg-gray-900 text-white">
    <div class="max-w-7xl mx-auto px-6 pt-16 pb-10">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-10">
        <!-- Brand -->
        <div class="md:col-span-1 flex flex-col gap-5">
          <div class="flex items-center gap-2.5">
            <div class="w-9 h-9 bg-rose-400 rounded-xl flex items-center justify-center">
              <span class="text-white text-base">🍼</span>
            </div>
            <div class="flex flex-col leading-none">
              <span style="font-family: 'Playfair Display', serif;" class="text-lg font-bold text-white">Yasmim <span class="text-rose-400">& Hércules</span></span>
              <span class="text-[10px] text-gray-500 uppercase tracking-widest">Fotografia</span>
            </div>
          </div>
          <p class="text-gray-400 text-sm leading-relaxed">Especializados em fotografia de gestante, newborn e família. Desde 2009, eternizando os momentos mais preciosos.</p>
          <div class="flex gap-3">
            <a v-for="s in socials" :key="s.label" :href="s.href" target="_blank" :aria-label="s.label"
              class="w-9 h-9 bg-gray-800 hover:bg-rose-400 rounded-xl flex items-center justify-center text-gray-400 hover:text-white transition-all duration-200 hover:scale-110">
              {{ s.icon }}
            </a>
          </div>
          <a href="https://wa.me/5561982514499" target="_blank"
            class="inline-flex items-center gap-2 bg-emerald-600 hover:bg-emerald-500 text-white rounded-xl px-4 py-2.5 text-sm font-semibold transition-all w-fit">
            💬 (61) 98251-4499
          </a>
        </div>

        <!-- Navegação -->
        <div class="flex flex-col gap-4">
          <h4 class="text-xs font-semibold uppercase tracking-widest text-gray-500">Navegação</h4>
          <nav class="flex flex-col gap-2">
            <a v-for="item in navLinks" :key="item" class="text-gray-400 hover:text-rose-400 text-sm transition-colors">{{ item }}</a>
          </nav>
        </div>

        <!-- Serviços -->
        <div class="flex flex-col gap-4">
          <h4 class="text-xs font-semibold uppercase tracking-widest text-gray-500">Especialidades</h4>
          <ul class="flex flex-col gap-2">
            <li v-for="s in specialties" :key="s" class="text-gray-400 text-sm flex items-center gap-2">
              <span class="w-1 h-1 rounded-full bg-rose-400 flex-shrink-0" />{{ s }}
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="border-t border-gray-800" />
    <div class="max-w-7xl mx-auto px-6 py-5 flex flex-col sm:flex-row items-center justify-between gap-3">
      <p class="text-gray-600 text-sm">© {{ year }} Yasmim & Hércules Fotografia. Todos os direitos reservados.</p>
      <p class="text-gray-700 text-sm flex items-center gap-1">Feito com <span class="text-rose-400">💕</span> em Brasília – DF</p>
    </div>
  </footer>
</template>

<script setup lang="ts">
const year = new Date().getFullYear()
const socials = [
  { label: 'Instagram', icon: '📸', href: 'https://instagram.com/yasmimeherculesfotografia' },
  { label: 'Facebook',  icon: '📘', href: 'https://facebook.com' },
  { label: 'YouTube',   icon: '▶️', href: 'https://youtube.com'  },
]
const navLinks    = ['Início', 'Sobre', 'Portfólio', 'Contato']
const specialties = ['Newborn', 'Ensaio de Gestante', 'Fotografia de Bebê', 'Família', 'Ensaio Temático', 'Aniversário']
</script>
