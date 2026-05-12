<template>
  <div class="min-h-screen bg-white text-gray-900 font-sans">
    <Head>
      <Title>Yasmim e Hércules Fotografia — Newborn, Gestante & Família</Title>
      <Meta name="description" content="Fotografia especializada em newborn, gestante e família. Desde 2009, capturando os primeiros e mais preciosos momentos da sua família." />
      <Link rel="preconnect" href="https://fonts.googleapis.com" />
      <Link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet" />
    </Head>

    <YasminHeader />

    <main>
      <!-- =========================================================
           SEÇÃO HERO
      ========================================================== -->
      <section id="inicio" class="relative min-h-screen flex items-center overflow-hidden bg-rose-50">
        <!-- Gradiente decorativo -->
        <div class="absolute inset-0 pointer-events-none">
          <div class="absolute top-0 right-0 w-[55%] h-full bg-gradient-to-l from-pink-50 via-rose-50/60 to-transparent" />
          <div class="absolute -bottom-20 -left-20 w-96 h-96 bg-pink-100 rounded-full opacity-40 blur-3xl" />
        </div>

        <div class="relative max-w-7xl mx-auto px-6 pt-28 pb-16 grid grid-cols-1 lg:grid-cols-2 gap-12 items-center w-full">
          <!-- Texto -->
          <div class="flex flex-col gap-7">
            <div class="inline-flex items-center gap-2 bg-rose-100 border border-rose-200 text-rose-700 text-xs font-semibold uppercase tracking-widest px-4 py-1.5 rounded-full w-fit">
              <span class="w-1.5 h-1.5 bg-rose-500 rounded-full animate-pulse" />
              Newborn · Gestante · Bebê · Família
            </div>

            <h1 style="font-family: 'Playfair Display', serif;" class="text-6xl md:text-7xl font-bold leading-[1.05] text-gray-900">
              Os primeiros<br />
              <em class="not-italic text-rose-400">instantes</em>
              <span class="text-gray-300"> que</span><br />
              ficam
            </h1>

            <p class="text-gray-500 text-lg leading-relaxed max-w-md">
              Especializados em fotografia de gestante, newborn e família.
              Capturando com amor cada detalhe dos momentos mais preciosos da sua vida.
            </p>

            <div class="flex flex-wrap gap-4 mt-2">
              <a href="https://wa.me/5561982514499" target="_blank"
                class="inline-flex items-center gap-2 bg-rose-500 hover:bg-rose-400 text-white font-semibold px-8 py-3.5 rounded-xl transition-all duration-200 hover:scale-105 shadow-lg shadow-rose-500/20 text-base">
                Agendar sessão →
              </a>
              <button class="inline-flex items-center gap-2 border-2 border-rose-400 text-rose-500 hover:bg-rose-50 font-semibold px-7 py-3 rounded-xl transition-all duration-200 text-base">
                Ver portfólio
              </button>
            </div>

            <div class="flex gap-8 pt-4 border-t border-rose-100 mt-2">
              <div v-for="stat in stats" :key="stat.label">
                <p style="font-family: 'Playfair Display', serif;" class="text-3xl font-bold text-gray-900">{{ stat.value }}</p>
                <p class="text-xs text-gray-500 mt-0.5">{{ stat.label }}</p>
              </div>
            </div>
          </div>

          <!-- Foto + cards flutuantes -->
          <div class="relative flex items-center justify-center lg:justify-end">
            <div class="relative z-10 w-full max-w-md">
              <div class="relative overflow-hidden rounded-3xl shadow-2xl shadow-rose-200 aspect-[3/4]">
                <img src="/yasmin_hero.png" alt="Newborn photography" class="w-full h-full object-cover" />
                <div class="absolute inset-0 bg-gradient-to-t from-gray-900/25 via-transparent to-transparent" />
              </div>

              <!-- Card flutuante - desde -->
              <div class="absolute -bottom-6 -left-6 bg-white rounded-2xl shadow-xl shadow-rose-100 p-4 flex items-center gap-3 animate-float">
                <div class="w-10 h-10 bg-rose-100 rounded-xl flex items-center justify-center text-lg">🍼</div>
                <div>
                  <p class="font-semibold text-gray-900 text-sm">+3.000 ensaios</p>
                  <div class="flex text-rose-400 text-xs mt-0.5">★★★★★</div>
                </div>
              </div>

              <!-- Card flutuante - desde 2009 -->
              <div class="absolute -top-4 -right-4 bg-white rounded-2xl shadow-xl shadow-rose-100 px-4 py-3 animate-float" style="animation-delay: 1.5s">
                <p class="text-xs text-gray-500 font-medium">📅 No mercado desde</p>
                <p style="font-family: 'Playfair Display', serif;" class="font-bold text-gray-900 text-lg leading-none">2009</p>
              </div>
            </div>

            <!-- Decoração -->
            <div class="absolute top-8 right-0 w-72 h-72 rounded-full border-2 border-dashed border-rose-100 opacity-70" />
            <div class="absolute top-16 right-8 w-56 h-56 rounded-full border border-pink-200/50" />
          </div>
        </div>

        <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-rose-300 animate-bounce">
          <p class="text-xs uppercase tracking-widest font-medium">Rolar</p>
          <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
          </svg>
        </div>
      </section>

      <!-- FAIXA -->
      <div class="bg-rose-400 py-5">
        <div class="flex items-center gap-10 px-6 max-w-7xl mx-auto justify-between flex-wrap">
          <span v-for="item in services" :key="item" class="text-white/90 text-sm font-medium flex items-center gap-2">
            <span class="w-1 h-1 bg-white/60 rounded-full" />{{ item }}
          </span>
        </div>
      </div>

      <!-- =========================================================
           SEÇÃO SOBRE
      ========================================================== -->
      <section id="sobre" class="py-28 bg-rose-50 overflow-hidden">
        <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
          <div class="flex flex-col gap-7">
            <div class="inline-flex items-center gap-2 w-fit">
              <span class="h-px w-8 bg-rose-300" />
              <span class="text-rose-500 text-xs font-semibold uppercase tracking-widest">Sobre nós</span>
            </div>
            <h2 style="font-family: 'Playfair Display', serif;" class="text-5xl md:text-6xl font-bold text-gray-900 leading-[1.1]">
              Amor em<br />cada<br /><em class="not-italic text-rose-400">clique</em>
            </h2>
            <p class="text-gray-600 text-xl font-light leading-relaxed">
              Somos Yasmim e Hércules — um casal apaixonado por fotografia de gestante, bebê e família desde 2009.
            </p>
            <p class="text-gray-500 leading-relaxed">
              Com mais de <strong class="text-gray-700 font-semibold">15 anos</strong> de experiência e mais de
              <strong class="text-gray-700 font-semibold">3.000 ensaios</strong> realizados, nossa missão é eternizar
              os primeiros e mais preciosos momentos da sua família com sensibilidade e técnica impecável.
            </p>
            <ul class="grid grid-cols-1 sm:grid-cols-2 gap-3">
              <li v-for="feat in features" :key="feat.label" class="flex items-center gap-3 bg-white rounded-xl px-4 py-3 shadow-sm border border-rose-100">
                <span class="text-xl">{{ feat.icon }}</span>
                <span class="text-sm font-medium text-gray-700">{{ feat.label }}</span>
              </li>
            </ul>
            <div class="flex gap-4 mt-2">
              <a href="https://wa.me/5561982514499" target="_blank"
                class="inline-flex items-center gap-2 bg-rose-500 hover:bg-rose-400 text-white font-semibold px-7 py-3 rounded-xl transition-all duration-200 hover:scale-105 shadow-lg shadow-rose-500/20">
                Agendar sessão →
              </a>
            </div>
          </div>

          <div class="relative flex items-center justify-center">
            <div class="absolute top-6 left-6 w-full h-full rounded-3xl border-2 border-dashed border-rose-200" />
            <div class="relative z-10 w-full max-w-sm">
              <div class="overflow-hidden rounded-3xl shadow-2xl shadow-rose-200 aspect-[3/4]">
                <img src="/yp2.png" alt="Yasmim e Hércules Fotografia" class="w-full h-full object-cover hover:scale-105 transition-transform duration-700" />
                <div class="absolute inset-0 bg-gradient-to-t from-gray-900/30 via-transparent to-transparent" />
              </div>
              <div class="absolute -bottom-5 -right-5 bg-rose-500 text-white rounded-2xl shadow-lg p-5 text-center">
                <p style="font-family: 'Playfair Display', serif;" class="text-4xl font-bold leading-none">15+</p>
                <p class="text-rose-100 text-xs mt-1 font-medium leading-tight">anos de<br />experiência</p>
              </div>
              <div class="absolute -top-5 -left-5 bg-white rounded-2xl shadow-xl px-4 py-3 flex items-center gap-3">
                <div class="text-2xl">🏅</div>
                <div>
                  <p class="text-gray-900 font-semibold text-sm leading-none">10,2 mil</p>
                  <p class="text-gray-400 text-xs mt-0.5">seguidores</p>
                </div>
              </div>
            </div>
            <div class="absolute bottom-0 right-0 w-56 h-56 rounded-full border border-pink-200 -z-0" />
          </div>
        </div>
      </section>

      <!-- =========================================================
           SEÇÃO PORTFÓLIO
      ========================================================== -->
      <section id="portfolio" class="py-28 bg-white overflow-hidden">
        <div class="max-w-7xl mx-auto px-6">
          <div class="text-center mb-16 max-w-2xl mx-auto">
            <div class="inline-flex items-center gap-3 mb-5">
              <span class="h-px w-10 bg-rose-200" />
              <span class="text-rose-500 text-xs font-semibold uppercase tracking-widest">Portfólio</span>
              <span class="h-px w-10 bg-rose-200" />
            </div>
            <h2 style="font-family: 'Playfair Display', serif;" class="text-5xl md:text-6xl font-bold text-gray-900 leading-tight mb-5">
              Momentos que<br />a gente <em class="not-italic text-rose-400">nunca esquece</em>
            </h2>
            <p class="text-gray-500 text-lg leading-relaxed">Cada foto é uma memória que vai durar para sempre.</p>
          </div>

          <!-- Galeria masonry -->
          <div class="columns-1 sm:columns-2 lg:columns-3 gap-4 space-y-4">
            <div v-for="(photo, i) in portfolio" :key="photo.id"
              class="break-inside-avoid group relative overflow-hidden rounded-2xl cursor-pointer shadow-sm hover:shadow-xl hover:shadow-rose-100 transition-all duration-500 hover:-translate-y-1"
              @click="lightboxIndex = i; lightboxOpen = true">
              <img :src="photo.src" :alt="photo.title"
                :class="['w-full object-cover transition-transform duration-700 group-hover:scale-105', photo.tall ? 'aspect-[3/4]' : 'aspect-[4/3]']" loading="lazy" />
              <div class="absolute inset-0 bg-gradient-to-t from-gray-900/70 via-gray-900/10 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-400 flex flex-col justify-end p-5">
                <div class="translate-y-4 group-hover:translate-y-0 transition-transform duration-400">
                  <span class="text-xs font-semibold uppercase tracking-widest text-rose-300 mb-1 block">{{ photo.category }}</span>
                  <h3 class="text-white font-semibold text-lg leading-tight">{{ photo.title }}</h3>
                </div>
              </div>
            </div>
          </div>

          <div class="text-center mt-16">
            <a href="https://wa.me/5561982514499" target="_blank"
              class="inline-flex items-center gap-2 bg-rose-500 hover:bg-rose-400 text-white font-semibold px-8 py-4 rounded-xl transition-all duration-200 hover:scale-105 shadow-lg shadow-rose-500/20 text-base">
              Quero agendar meu ensaio →
            </a>
          </div>
        </div>
      </section>

      <!-- =========================================================
           SEÇÃO CONTATO
      ========================================================== -->
      <section id="contato" class="py-28 bg-rose-50 overflow-hidden">
        <div class="max-w-7xl mx-auto px-6">
          <div class="text-center mb-16">
            <div class="inline-flex items-center gap-3 mb-5">
              <span class="h-px w-10 bg-rose-200" />
              <span class="text-rose-500 text-xs font-semibold uppercase tracking-widest">Contato</span>
              <span class="h-px w-10 bg-rose-200" />
            </div>
            <h2 style="font-family: 'Playfair Display', serif;" class="text-5xl md:text-6xl font-bold text-gray-900 leading-tight">
              Vamos eternizar<br /><em class="not-italic text-rose-400">sua história?</em>
            </h2>
          </div>

          <div class="grid grid-cols-1 lg:grid-cols-2 gap-10 items-start">
            <!-- Infos + mapa -->
            <div class="flex flex-col gap-7">
              <p class="text-gray-500 text-lg leading-relaxed">
                Fale conosco para agendar seu ensaio de newborn, gestante, bebê ou família. Atendemos com todo o carinho que o seu momento merece. 💕
              </p>
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                <a v-for="info in contactInfos" :key="info.label" :href="info.href" target="_blank"
                  class="group flex items-center gap-4 bg-white rounded-2xl p-5 shadow-sm border border-rose-100 hover:shadow-md hover:-translate-y-0.5 transition-all duration-300">
                  <div :class="['w-12 h-12 rounded-xl flex items-center justify-center text-xl flex-shrink-0', info.bg]">{{ info.icon }}</div>
                  <div class="min-w-0">
                    <p class="text-xs font-semibold uppercase tracking-wider text-gray-400 mb-0.5">{{ info.label }}</p>
                    <p class="text-gray-800 font-semibold text-sm truncate group-hover:text-rose-500 transition-colors">{{ info.value }}</p>
                  </div>
                </a>
              </div>
              <div class="overflow-hidden rounded-3xl shadow-md border border-rose-100">
                <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3838.2!2d-47.9297!3d-15.7801!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x935a3b70fb59c9d7%3A0x8b97f6b99d9b9b5a!2sBras%C3%ADlia%2C%20DF!5e0!3m2!1spt-BR!2sbr!4v1715000000000"
                  width="100%" height="280" style="border:0;" allowfullscreen="" loading="lazy"
                  class="grayscale hover:grayscale-0 transition-all duration-500" />
              </div>
            </div>

            <!-- Formulário -->
            <div class="bg-white rounded-3xl shadow-xl shadow-rose-100 border border-rose-100 p-8 md:p-10">
              <h3 style="font-family: 'Playfair Display', serif;" class="text-3xl font-bold text-gray-900 mb-2">Envie uma mensagem</h3>
              <p class="text-gray-400 text-sm mb-8">Respondemos rapidinho 💕</p>
              <form class="flex flex-col gap-5" @submit.prevent="submitForm">
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
                  <BaseInput v-model="form.nome" label="Seu nome" placeholder="Ana Beatriz" icon-left="👤" required :error="errors.nome" />
                  <BaseInput v-model="form.telefone" label="WhatsApp" placeholder="(61) 99999-9999" icon-left="📱" type="tel" required :error="errors.telefone" />
                </div>
                <BaseInput v-model="form.email" label="E-mail" placeholder="ana@email.com" icon-left="✉️" type="email" :error="errors.email" />
                <div class="flex flex-col gap-1.5">
                  <label class="text-sm font-medium text-gray-700">Tipo de ensaio <span class="text-rose-400">*</span></label>
                  <div class="flex flex-wrap gap-2">
                    <button v-for="srv in servicos" :key="srv" type="button"
                      :class="['px-4 py-2 rounded-xl text-sm font-medium transition-all duration-200 border', form.servico === srv ? 'bg-rose-500 border-rose-500 text-white' : 'bg-rose-50 border-rose-100 text-gray-600 hover:border-rose-300 hover:text-rose-600']"
                      @click="form.servico = srv">{{ srv }}</button>
                  </div>
                </div>
                <BaseInput v-model="form.mensagem" label="Conta um pouco sobre seu ensaio" placeholder="Ex: Estou esperando meu bebê para março e quero um ensaio newborn..." type="textarea" :rows="4" required :error="errors.mensagem" />
                <button type="submit"
                  :disabled="sending"
                  class="w-full flex items-center justify-center gap-2 bg-rose-500 hover:bg-rose-400 disabled:opacity-50 text-white font-semibold px-6 py-3.5 rounded-xl transition-all duration-200 mt-2">
                  <span v-if="sending" class="inline-block w-4 h-4 border-2 border-white border-t-transparent rounded-full animate-spin" />
                  {{ sending ? 'Enviando...' : 'Enviar mensagem →' }}
                </button>
                <Transition enter-active-class="transition-all duration-400" enter-from-class="opacity-0 translate-y-2" enter-to-class="opacity-100 translate-y-0">
                  <div v-if="sent" class="flex items-center gap-3 bg-emerald-50 border border-emerald-200 text-emerald-700 rounded-xl px-5 py-4 text-sm font-medium">
                    <span class="text-xl">✅</span> Mensagem enviada! Entraremos em contato em breve. 💕
                  </div>
                </Transition>
              </form>
            </div>
          </div>
        </div>
      </section>

      <YasminFooter />
    </main>

    <!-- Lightbox simples -->
    <Teleport to="body">
      <Transition enter-active-class="transition-opacity duration-300" enter-from-class="opacity-0" enter-to-class="opacity-100" leave-active-class="transition-opacity duration-200" leave-from-class="opacity-100" leave-to-class="opacity-0">
        <div v-if="lightboxOpen" class="fixed inset-0 z-[100] bg-black/90 flex items-center justify-center p-4" @click.self="lightboxOpen = false">
          <button class="absolute top-4 right-4 text-white/70 hover:text-white text-3xl w-10 h-10 flex items-center justify-center" @click="lightboxOpen = false">✕</button>
          <img :src="portfolio[lightboxIndex]?.src" :alt="portfolio[lightboxIndex]?.title" class="max-h-[85vh] max-w-full object-contain rounded-2xl" />
        </div>
      </Transition>
    </Teleport>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

const stats = [
  { value: '15+',  label: 'Anos de experiência' },
  { value: '3k+',  label: 'Ensaios realizados'  },
  { value: '10,2k',label: 'Seguidores'           },
]

const features = [
  { icon: '👶', label: 'Especialistas em Newborn' },
  { icon: '🤰', label: 'Ensaio de Gestante'       },
  { icon: '👨‍👩‍👧', label: 'Fotografia de Família'   },
  { icon: '🌸', label: 'Estúdio temático'          },
  { icon: '📷', label: 'Fotografia profissional'   },
  { icon: '💌', label: 'Entrega digital'           },
]

const services = ['Newborn', 'Gestante', 'Bebê', 'Família', 'Aniversário', 'Ensaio Temático']

const contactInfos = [
  { icon: '📱', label: 'WhatsApp', bg: 'bg-emerald-50 text-emerald-600', value: '(61) 98251-4499', href: 'https://wa.me/5561982514499' },
  { icon: '📸', label: 'Instagram', bg: 'bg-pink-50 text-pink-600', value: '@yasmimeherculesfotografia', href: 'https://instagram.com/yasmimeherculesfotografia' },
  { icon: '✉️', label: 'E-mail', bg: 'bg-rose-50 text-rose-600', value: 'contato@yasmimehercules.com', href: 'mailto:contato@yasmimehercules.com' },
  { icon: '📍', label: 'Localização', bg: 'bg-gray-100 text-gray-600', value: 'Brasília – DF', href: 'https://maps.google.com' },
]

const servicos = ['Newborn', 'Gestante', 'Bebê', 'Família', 'Aniversário', 'Outro']

const portfolio = [
  { id: 1, src: '/yp1.png', title: 'Newborn Suave',   category: 'Newborn',  tall: true  },
  { id: 2, src: '/yp2.png', title: 'Amor de Família', category: 'Família',  tall: false },
  { id: 3, src: '/yp3.png', title: 'Gestante',        category: 'Gestante', tall: true  },
  { id: 4, src: '/yp4.png', title: 'Bebê Feliz',      category: 'Bebê',     tall: false },
  { id: 5, src: '/yasmin_hero.png', title: 'Newborn Especial', category: 'Newborn', tall: true },
]

const form    = reactive({ nome: '', telefone: '', email: '', servico: '', mensagem: '' })
const errors  = reactive({ nome: '', telefone: '', email: '', mensagem: '' })
const sending = ref(false)
const sent    = ref(false)
const lightboxOpen  = ref(false)
const lightboxIndex = ref(0)

function validate() {
  errors.nome     = form.nome.trim()     ? '' : 'Informe seu nome.'
  errors.telefone = form.telefone.trim() ? '' : 'Informe seu WhatsApp.'
  errors.email    = ''
  errors.mensagem = form.mensagem.trim() ? '' : 'Conte um pouco sobre seu ensaio.'
  return !Object.values(errors).some(Boolean)
}

async function submitForm() {
  if (!validate()) return
  sending.value = true
  await new Promise(r => setTimeout(r, 1800))
  sending.value = false
  sent.value    = true
  Object.keys(form).forEach(k => (form as Record<string, string>)[k] = '')
  setTimeout(() => { sent.value = false }, 6000)
}
</script>
