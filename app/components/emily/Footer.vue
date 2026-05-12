<template>
  <footer class="bg-stone-900 text-white">

    <!-- ── CORPO PRINCIPAL ── -->
    <div class="max-w-7xl mx-auto px-6 pt-20 pb-12">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-12">

        <!-- Col 1 — Brand -->
        <div class="lg:col-span-2 flex flex-col gap-6">
          <!-- Logo -->
          <div class="flex items-center gap-2.5">
            <div class="w-10 h-10 bg-brand-500 rounded-xl flex items-center justify-center shadow-warm-sm">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                <path stroke-linecap="round" stroke-linejoin="round" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z" />
                <path stroke-linecap="round" stroke-linejoin="round" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z" />
              </svg>
            </div>
            <div class="flex flex-col leading-none">
              <span class="font-serif text-xl font-bold tracking-tight">Emilly <span class="text-brand-400">& Pedro</span></span>
              <span class="text-[10px] text-stone-500 uppercase tracking-widest font-sans">Fotografia</span>
            </div>
          </div>

          <!-- Tagline -->
          <p class="text-stone-400 leading-relaxed max-w-sm">
            Capturando memórias que duram para sempre. 
            Fotografia de casamento, ensaios e eventos com alma e cuidado.
          </p>

          <!-- Redes sociais -->
          <div class="flex items-center gap-3">
            <a
              v-for="social in socials"
              :key="social.label"
              :href="social.href"
              target="_blank"
              :aria-label="social.label"
              class="w-10 h-10 bg-stone-800 hover:bg-brand-500 rounded-xl flex items-center justify-center text-stone-400 hover:text-white transition-all duration-200 hover:scale-110 hover:shadow-warm-sm"
            >
              <span class="text-base">{{ social.icon }}</span>
            </a>
          </div>

          <!-- WhatsApp CTA -->
          <a
            href="https://wa.me/5511999999999"
            target="_blank"
            class="inline-flex items-center gap-3 bg-emerald-600 hover:bg-emerald-500 text-white rounded-xl px-5 py-3 transition-all duration-200 hover:shadow-lg hover:scale-[1.02] w-fit"
          >
            <span class="text-lg">💬</span>
            <div>
              <p class="text-xs text-emerald-200 leading-none">Fale agora no</p>
              <p class="font-semibold text-sm leading-none mt-0.5">WhatsApp</p>
            </div>
          </a>
        </div>

        <!-- Col 2 — Navegação -->
        <div class="flex flex-col gap-5">
          <h4 class="text-xs font-semibold uppercase tracking-widest text-stone-500">Navegação</h4>
          <nav class="flex flex-col gap-3">
            <a
              v-for="item in navLinks"
              :key="item.label"
              :href="item.href"
              class="text-stone-400 hover:text-brand-400 text-sm font-medium transition-colors duration-200 flex items-center gap-2 group"
              @click.prevent="scrollTo(item.id)"
            >
              <span class="w-0 h-px bg-brand-400 group-hover:w-4 transition-all duration-200" />
              {{ item.label }}
            </a>
          </nav>
        </div>

        <!-- Col 3 — Serviços -->
        <div class="flex flex-col gap-5">
          <h4 class="text-xs font-semibold uppercase tracking-widest text-stone-500">Serviços</h4>
          <ul class="flex flex-col gap-3">
            <li
              v-for="srv in servicesList"
              :key="srv"
              class="text-stone-400 text-sm flex items-center gap-2"
            >
              <span class="w-1 h-1 rounded-full bg-brand-500 flex-shrink-0" />
              {{ srv }}
            </li>
          </ul>
        </div>

      </div>
    </div>

    <!-- ── DIVISOR ── -->
    <div class="border-t border-stone-800" />

    <!-- ── RODAPÉ INFERIOR ── -->
    <div class="max-w-7xl mx-auto px-6 py-6 flex flex-col sm:flex-row items-center justify-between gap-4">
      <p class="text-stone-600 text-sm text-center sm:text-left">
        © {{ currentYear }} Emilly & Pedro Fotografia. Todos os direitos reservados.
      </p>

      <div class="flex items-center gap-2 text-stone-600 text-sm">
        <span>Feito com</span>
        <span class="text-brand-500 animate-pulse">❤️</span>
        <span>em São Paulo</span>
      </div>
    </div>

  </footer>
</template>

<script setup lang="ts">
const currentYear = new Date().getFullYear()

const socials = [
  { label: 'Instagram', icon: '📸', href: 'https://instagram.com' },
  { label: 'Facebook',  icon: '📘', href: 'https://facebook.com'  },
  { label: 'Pinterest', icon: '📌', href: 'https://pinterest.com' },
  { label: 'YouTube',   icon: '▶️', href: 'https://youtube.com'   },
]

const navLinks = [
  { label: 'Início',    id: 'inicio',    href: '#inicio'    },
  { label: 'Sobre',     id: 'sobre',     href: '#sobre'     },
  { label: 'Portfólio', id: 'portfolio', href: '#portfolio' },
  { label: 'Contato',   id: 'contato',   href: '#contato'   },
]

const servicesList = [
  'Casamento Civil',
  'Casamento Religioso',
  'Ensaio de Casal',
  'Pré-Wedding',
  'Chá de Panela',
  'Ensaio Gestante',
  'Eventos Corporativos',
]

function scrollTo(id: string) {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth', block: 'start' })
}
</script>
