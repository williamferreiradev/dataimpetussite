<template>
  <div class="min-h-screen bg-stone-50 text-stone-900 font-sans">
    <Head>
      <Title>Emilly & Pedro Fotografia — Casamentos, Ensaios e Eventos</Title>
      <Meta name="description" content="Fotografia de casamento, ensaios românticos e eventos em São Paulo. Cada clique é eterno." />
      <Link rel="preconnect" href="https://fonts.googleapis.com" />
      <Link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="" />
      <Link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,600;0,700;1,400;1,600&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet" />
    </Head>

    <EmilyHeader />

    <main>
      <!-- =========================================================
           SEÇÃO HERO — HOME
      ========================================================== -->
      <section id="inicio" class="relative min-h-screen flex items-center overflow-hidden bg-stone-50">
        <div class="absolute inset-0 pointer-events-none">
          <div class="absolute top-0 right-0 w-[60%] h-full bg-gradient-to-l from-brand-50 via-stone-100/60 to-transparent" />
          <div class="absolute bottom-0 left-0 w-96 h-96 bg-gradient-radial from-gold-300/20 to-transparent rounded-full blur-3xl" />
        </div>

        <div class="relative max-w-7xl mx-auto px-6 pt-28 pb-16 grid grid-cols-1 lg:grid-cols-2 gap-12 items-center w-full">
          <div class="flex flex-col gap-7 animate-fade-up">
            <div class="inline-flex items-center gap-2 bg-brand-100 border border-brand-200 text-brand-700 text-xs font-semibold uppercase tracking-widest px-4 py-1.5 rounded-full w-fit">
              <span class="w-1.5 h-1.5 bg-brand-500 rounded-full animate-pulse" />
              Fotografia de casamento · Ensaios · Eventos
            </div>
            <h1 class="font-serif text-6xl md:text-7xl font-bold leading-[1.05] text-stone-900">
              Momentos que<br />
              <em class="not-italic text-brand-500">contam</em>
              <span class="text-stone-300"> sua</span><br />
              história
            </h1>
            <p class="text-stone-500 text-lg leading-relaxed max-w-md">
              Fotografia autoral com olhar sensível e técnica impecável.
              Do civil ao grande dia — cada clique é eterno.
            </p>
            <div class="flex flex-wrap gap-4 mt-2">
              <BaseButton variant="primary" size="lg" icon-right="→">Ver portfólio</BaseButton>
              <BaseButton variant="outline" size="lg">Agendar sessão</BaseButton>
            </div>
            <div class="flex gap-8 pt-4 border-t border-stone-200 mt-2">
              <div v-for="stat in stats" :key="stat.label">
                <p class="font-serif text-3xl font-bold text-stone-900">{{ stat.value }}</p>
                <p class="text-xs text-stone-500 mt-0.5">{{ stat.label }}</p>
              </div>
            </div>
          </div>

          <div class="relative flex items-center justify-center lg:justify-end animate-fade-in">
            <div class="relative z-10 w-full max-w-md">
              <div class="relative overflow-hidden rounded-3xl shadow-warm-lg aspect-[3/4]">
                <img src="/hero.png" alt="Fotografia de casamento" class="w-full h-full object-cover" />
                <div class="absolute inset-0 bg-gradient-to-t from-stone-900/30 via-transparent to-transparent" />
              </div>
              <div class="absolute -bottom-6 -left-6 bg-white rounded-2xl shadow-card-hover p-4 flex items-center gap-3 animate-float">
                <div class="w-10 h-10 bg-brand-100 rounded-xl flex items-center justify-center text-lg">⭐</div>
                <div>
                  <p class="font-semibold text-stone-900 text-sm">+200 casais felizes</p>
                  <div class="flex text-gold-500 text-xs mt-0.5">★★★★★</div>
                </div>
              </div>
              <div class="absolute -top-4 -right-4 bg-white rounded-2xl shadow-card-hover px-4 py-3 animate-float" style="animation-delay: 1.5s">
                <p class="text-xs text-stone-500 font-medium">📦 Entrega em</p>
                <p class="font-serif font-bold text-stone-900 text-lg leading-none">24 horas</p>
              </div>
            </div>
            <div class="absolute top-8 right-0 w-80 h-80 rounded-full border-2 border-dashed border-brand-100 opacity-60" />
            <div class="absolute top-16 right-8 w-64 h-64 rounded-full border border-gold-300/40" />
          </div>
        </div>

        <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-stone-400 animate-bounce">
          <p class="text-xs uppercase tracking-widest font-medium">Rolar</p>
          <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
          </svg>
        </div>
      </section>

      <!-- FAIXA -->
      <div class="bg-brand-500 py-5">
        <div class="flex items-center gap-12 whitespace-nowrap px-6 max-w-7xl mx-auto justify-between flex-wrap">
          <span v-for="item in services" :key="item" class="text-white/90 font-sans text-sm font-medium flex items-center gap-2">
            <span class="w-1 h-1 bg-white/50 rounded-full" />{{ item }}
          </span>
        </div>
      </div>

      <!-- =========================================================
           SEÇÃO SOBRE
      ========================================================== -->
      <section id="sobre" class="py-28 bg-stone-100 overflow-hidden">
        <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
          <div class="flex flex-col gap-7">
            <div class="inline-flex items-center gap-2 w-fit">
              <span class="h-px w-8 bg-brand-400" />
              <span class="text-brand-500 text-xs font-semibold uppercase tracking-widest">Sobre mim</span>
            </div>
            <h2 class="font-serif text-5xl md:text-6xl font-bold text-stone-900 leading-[1.1]">
              Uma história<br />contada com<br /><em class="not-italic text-brand-500">luz e amor</em>
            </h2>
            <p class="text-stone-600 text-xl font-light leading-relaxed">
              Fotógrafa especializada em casamentos e ensaios românticos, com olhar artístico e alma apaixonada por histórias reais.
            </p>
            <p class="text-stone-500 leading-relaxed">
              Há mais de <strong class="text-stone-700 font-semibold">10 anos</strong> capturando sorrisos, lágrimas de alegria e abraços que a gente nunca quer largar.
            </p>
            <ul class="grid grid-cols-1 sm:grid-cols-2 gap-3">
              <li v-for="feat in features" :key="feat.label" class="flex items-center gap-3 bg-white rounded-xl px-4 py-3 shadow-card">
                <span class="text-xl">{{ feat.icon }}</span>
                <span class="text-sm font-medium text-stone-700">{{ feat.label }}</span>
              </li>
            </ul>
            <div class="flex gap-4 mt-2">
              <BaseButton variant="primary" size="lg" icon-right="→">Agendar sessão</BaseButton>
              <BaseButton variant="ghost" size="lg">Ver portfólio</BaseButton>
            </div>
          </div>

          <div class="relative flex items-center justify-center">
            <div class="absolute top-6 left-6 w-full h-full rounded-3xl border-2 border-dashed border-brand-200" />
            <div class="relative z-10 w-full max-w-sm">
              <div class="overflow-hidden rounded-3xl shadow-warm-lg aspect-[3/4]">
                <img src="/sobre.png" alt="Fotógrafa profissional" class="w-full h-full object-cover hover:scale-105 transition-transform duration-700" />
                <div class="absolute inset-0 bg-gradient-to-t from-stone-900/40 via-transparent to-transparent" />
              </div>
              <div class="absolute -bottom-5 -right-5 bg-brand-500 text-white rounded-2xl shadow-warm-md p-5 text-center">
                <p class="font-serif text-4xl font-bold leading-none">10+</p>
                <p class="text-brand-100 text-xs mt-1 font-medium leading-tight">anos de<br />experiência</p>
              </div>
              <div class="absolute -top-5 -left-5 bg-white rounded-2xl shadow-card-hover px-4 py-3 flex items-center gap-3">
                <div class="text-2xl">🏆</div>
                <div>
                  <p class="text-stone-900 font-semibold text-sm leading-none">Premiada</p>
                  <p class="text-stone-400 text-xs mt-0.5">Fotografia editorial</p>
                </div>
              </div>
            </div>
            <div class="absolute bottom-0 right-0 w-56 h-56 rounded-full border border-gold-300/50 -z-0" />
            <div class="absolute bottom-10 right-10 w-36 h-36 rounded-full bg-brand-100/40 -z-0" />
          </div>
        </div>
      </section>

      <!-- =========================================================
           SEÇÃO PORTFÓLIO
      ========================================================== -->
      <section id="portfolio" class="py-28 bg-stone-50 overflow-hidden">
        <div class="max-w-7xl mx-auto px-6">
          <div class="text-center mb-16 max-w-2xl mx-auto">
            <div class="inline-flex items-center gap-3 mb-5">
              <span class="h-px w-10 bg-brand-300" />
              <span class="text-brand-500 text-xs font-semibold uppercase tracking-widest">Portfólio</span>
              <span class="h-px w-10 bg-brand-300" />
            </div>
            <h2 class="font-serif text-5xl md:text-6xl font-bold text-stone-900 leading-tight mb-5">
              Cada foto,<br />uma <em class="not-italic text-brand-500">eternidade</em>
            </h2>
            <p class="text-stone-500 text-lg leading-relaxed">
              Uma seleção cuidadosa dos momentos que tive o privilégio de capturar.
            </p>
          </div>
          <EmilyGallery />
          <div class="text-center mt-16 flex flex-col items-center gap-5">
            <p class="text-stone-500 text-sm">Gostou do que viu? <span class="text-stone-700 font-semibold">Vamos criar sua história juntos.</span></p>
            <BaseButton variant="primary" size="lg" icon-right="→">Agendar minha sessão</BaseButton>
          </div>
        </div>
      </section>

      <!-- =========================================================
           SEÇÃO CONTATO
      ========================================================== -->
      <section id="contato" class="py-28 bg-stone-100 overflow-hidden">
        <div class="max-w-7xl mx-auto px-6">
          <div class="text-center mb-16">
            <div class="inline-flex items-center gap-3 mb-5">
              <span class="h-px w-10 bg-brand-300" />
              <span class="text-brand-500 text-xs font-semibold uppercase tracking-widest">Contato</span>
              <span class="h-px w-10 bg-brand-300" />
            </div>
            <h2 class="font-serif text-5xl md:text-6xl font-bold text-stone-900 leading-tight">
              Vamos criar algo<br /><em class="not-italic text-brand-500">inesquecível</em> juntos?
            </h2>
          </div>

          <div class="grid grid-cols-1 lg:grid-cols-2 gap-10 items-start">
            <div class="flex flex-col gap-7">
              <p class="text-stone-500 text-lg leading-relaxed">Seja para um casamento dos sonhos, ensaio romântico ou evento especial — estou pronta para ouvir sua história.</p>
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                <a v-for="info in contactInfos" :key="info.label" :href="info.href" target="_blank"
                  class="group flex items-center gap-4 bg-white rounded-2xl p-5 shadow-card hover:shadow-card-hover hover:-translate-y-0.5 transition-all duration-300">
                  <div :class="['w-12 h-12 rounded-xl flex items-center justify-center text-xl flex-shrink-0', info.bg]">{{ info.icon }}</div>
                  <div class="min-w-0">
                    <p class="text-xs font-semibold uppercase tracking-wider text-stone-400 mb-0.5">{{ info.label }}</p>
                    <p class="text-stone-800 font-semibold text-sm truncate group-hover:text-brand-600 transition-colors">{{ info.value }}</p>
                  </div>
                </a>
              </div>
              <div class="overflow-hidden rounded-3xl shadow-warm-md border border-stone-200">
                <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3657.075!2d-46.6395!3d-23.5505!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x94ce59c8da0aa315%3A0xd59f9431f2c9776a!2sAv.%20Paulista%2C%20S%C3%A3o%20Paulo!5e0!3m2!1spt-BR!2sbr!4v1715000000000"
                  width="100%" height="280" style="border:0;" allowfullscreen="" loading="lazy" class="grayscale hover:grayscale-0 transition-all duration-500" />
              </div>
            </div>

            <div class="bg-white rounded-3xl shadow-card-hover p-8 md:p-10">
              <h3 class="font-serif text-3xl font-bold text-stone-900 mb-2">Envie uma mensagem</h3>
              <p class="text-stone-400 text-sm mb-8">Respondo em até 2 horas 🤍</p>
              <form class="flex flex-col gap-5" @submit.prevent="submitForm">
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-5">
                  <BaseInput v-model="form.nome" label="Seu nome" placeholder="Maria Silva" icon-left="👤" required :error="errors.nome" />
                  <BaseInput v-model="form.telefone" label="WhatsApp" placeholder="(11) 99999-9999" icon-left="📱" type="tel" required :error="errors.telefone" />
                </div>
                <BaseInput v-model="form.email" label="E-mail" placeholder="maria@email.com" icon-left="✉️" type="email" required :error="errors.email" />
                <div class="flex flex-col gap-1.5">
                  <label class="text-sm font-medium text-stone-700">Tipo de serviço <span class="text-rose-400">*</span></label>
                  <div class="flex flex-wrap gap-2">
                    <button v-for="srv in servicos" :key="srv" type="button"
                      :class="['px-4 py-2 rounded-xl text-sm font-medium transition-all duration-200 border', form.servico === srv ? 'bg-brand-500 border-brand-500 text-white' : 'bg-stone-50 border-stone-200 text-stone-600 hover:border-brand-300 hover:text-brand-600']"
                      @click="form.servico = srv">{{ srv }}</button>
                  </div>
                </div>
                <BaseInput v-model="form.data" label="Data do evento (se tiver)" placeholder="dd/mm/aaaa" icon-left="📅" />
                <BaseInput v-model="form.mensagem" label="Conta um pouco sobre seu projeto" placeholder="Ex: Vou me casar em junho e sonho com fotos cheias de luz natural..." type="textarea" :rows="4" required :error="errors.mensagem" />
                <BaseButton type="submit" variant="primary" size="lg" :full="true" :loading="sending" icon-right="→" class="mt-2">
                  {{ sending ? 'Enviando...' : 'Enviar mensagem' }}
                </BaseButton>
                <Transition enter-active-class="transition-all duration-400" enter-from-class="opacity-0 translate-y-2" enter-to-class="opacity-100 translate-y-0">
                  <div v-if="sent" class="flex items-center gap-3 bg-emerald-50 border border-emerald-200 text-emerald-700 rounded-xl px-5 py-4 text-sm font-medium">
                    <span class="text-xl">✅</span> Mensagem enviada! Entro em contato em breve. 🤍
                  </div>
                </Transition>
              </form>
            </div>
          </div>
        </div>
      </section>

      <EmilyFooter />
    </main>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

const stats = [
  { value: '10+',  label: 'Anos de experiência' },
  { value: '200+', label: 'Casais fotografados'  },
  { value: '24h',  label: 'Entrega garantida'    },
]

const features = [
  { icon: '📷', label: 'Fotografia em RAW' },
  { icon: '🌅', label: 'Luz natural prioritária' },
  { icon: '📦', label: 'Entrega em 24 horas' },
  { icon: '🎬', label: 'Cobertura em vídeo' },
  { icon: '✏️', label: 'Edição artesanal' },
  { icon: '🤍', label: 'Sem limite de fotos' },
]

const services = ['Casamento Civil', 'Casamento Religioso', 'Ensaio de Casal', 'Chá de Panela', 'Pré-Wedding', 'Ensaio Gestante', 'Eventos Corporativos']

const contactInfos = [
  { icon: '📱', label: 'WhatsApp', bg: 'bg-emerald-50 text-emerald-600', value: '(11) 99999-9999', href: 'https://wa.me/5511999999999' },
  { icon: '📸', label: 'Instagram', bg: 'bg-pink-50 text-pink-600', value: '@emillyepedro.foto', href: 'https://instagram.com' },
  { icon: '✉️', label: 'E-mail', bg: 'bg-brand-50 text-brand-600', value: 'contato@emillyepedro.com', href: 'mailto:contato@emillyepedro.com' },
  { icon: '📍', label: 'Localização', bg: 'bg-stone-100 text-stone-600', value: 'São Paulo – SP', href: 'https://maps.google.com' },
]

const servicos = ['Casamento Civil', 'Casamento Religioso', 'Ensaio de Casal', 'Pré-Wedding', 'Evento', 'Outro']
const form     = reactive({ nome: '', telefone: '', email: '', servico: '', data: '', mensagem: '' })
const errors   = reactive({ nome: '', telefone: '', email: '', mensagem: '' })
const sending  = ref(false)
const sent     = ref(false)

function validate() {
  errors.nome     = form.nome.trim()     ? '' : 'Informe seu nome.'
  errors.telefone = form.telefone.trim() ? '' : 'Informe seu WhatsApp.'
  errors.email    = form.email.trim()    ? '' : 'Informe seu e-mail.'
  errors.mensagem = form.mensagem.trim() ? '' : 'Conte um pouco sobre seu projeto.'
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
