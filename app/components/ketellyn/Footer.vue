<template>
  <footer class="bg-gray-950 text-white">
    <div class="max-w-7xl mx-auto px-6 pt-16 pb-10">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-10">
        <div class="flex flex-col gap-5">
          <p style="font-family:'Playfair Display',serif;" class="text-xl font-bold">Ketellyn <span class="text-purple-400">Fotografias</span></p>
          <p class="text-gray-400 text-sm leading-relaxed">Apaixonada pela arte de fotografar a vida. Atendimentos em Padre Bernado e Brasília.</p>
          <div class="flex gap-3">
            <a href="https://instagram.com/ketellyn_fotografias" target="_blank" class="w-9 h-9 bg-gray-800 hover:bg-purple-600 rounded-xl flex items-center justify-center text-gray-400 hover:text-white transition-all duration-200">📸</a>
            <a href="https://facebook.com" target="_blank" class="w-9 h-9 bg-gray-800 hover:bg-purple-600 rounded-xl flex items-center justify-center text-gray-400 hover:text-white transition-all duration-200">📘</a>
          </div>
          <a href="https://wa.me/message/3HZOC5N3B6DGN1" target="_blank" class="inline-flex items-center gap-2 bg-emerald-600 hover:bg-emerald-500 text-white rounded-xl px-4 py-2.5 text-sm font-semibold w-fit">
            💬 Agendar agora
          </a>
        </div>
        <div class="flex flex-col gap-4">
          <h4 class="text-xs font-semibold uppercase tracking-widest text-gray-500">Navegação</h4>
          <nav class="flex flex-col gap-2">
            <span v-for="item in ['Início','Sobre','Portfólio','Contato']" :key="item" class="text-gray-400 hover:text-purple-400 text-sm transition-colors cursor-pointer">{{ item }}</span>
          </nav>
        </div>
        <div class="flex flex-col gap-4">
          <h4 class="text-xs font-semibold uppercase tracking-widest text-gray-500">Especialidades</h4>
          <ul class="flex flex-col gap-2">
            <li v-for="s in ['Gestante','Newborn','Família','Festa Infantil','15 Anos','Casamento','Ensaio Feminino','Formaturas']" :key="s" class="text-gray-400 text-sm flex items-center gap-2">
              <span class="w-1 h-1 rounded-full bg-purple-500 flex-shrink-0" />{{ s }}
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="border-t border-gray-800" />
    <div class="max-w-7xl mx-auto px-6 py-5 flex flex-col sm:flex-row items-center justify-between gap-3">
      <p class="text-gray-600 text-sm">© {{ new Date().getFullYear() }} Ketellyn Fotografias. Todos os direitos reservados.</p>
      <p class="text-gray-700 text-sm">Feito com 💜 em Padre Bernado – GO</p>
    </div>
  </footer>
</template>
