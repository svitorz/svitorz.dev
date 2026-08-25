<script setup>
import { onMounted, ref } from "vue";

const currentYear = new Date().getFullYear();
const isDark = ref(false);

const setTheme = (dark) => {
  isDark.value = dark;
  document.documentElement.classList.toggle("dark", dark);
  localStorage.setItem("theme", dark ? "dark" : "light");
};

const toggleTheme = () => setTheme(!isDark.value);

onMounted(() => {
  const savedTheme = localStorage.getItem("theme");
  const prefersDark = window.matchMedia("(prefers-color-scheme: dark)").matches;
  setTheme(savedTheme ? savedTheme === "dark" : prefersDark);
});
</script>

<template>
  <div class="site-shell">
    <header class="site-header">
      <a class="wordmark" href="#top" aria-label="Vitor Souza — início"><span class="wordmark-mark">VS</span><span>Vitor Souza</span></a>
      <nav aria-label="Navegação principal"><a href="#about">About</a><a href="#work">Work</a><a href="#writing">Writing</a><a class="nav-external" href="https://github.com/svitorz" target="_blank" rel="noreferrer">GitHub <span aria-hidden="true">↗</span></a><button class="theme-toggle" type="button" :aria-label="isDark ? 'Ativar modo claro' : 'Ativar modo escuro'" @click="toggleTheme"><span aria-hidden="true">{{ isDark ? '☼' : '◐' }}</span></button></nav>
    </header>

    <main id="top">
      <section class="intro" aria-labelledby="intro-title"><p class="eyebrow"><span class="status-dot" aria-hidden="true"></span> software developer · Votuporanga, SP</p><h1 id="intro-title">Vitor<br /><em>Souza.</em></h1><div class="intro-note"><span class="note-line" aria-hidden="true"></span><p>Desenvolvedor de software. Trabalho perto do backend, das APIs e das partes que fazem os sistemas continuarem de pé.</p></div></section>

      <div class="page-grid">
        <aside class="section-index" aria-label="Índice da página"><span>Índice</span><a href="#about">01 — sobre</a><a href="#work">02 — trabalho</a><a href="#formation">03 — formação</a><a href="#writing">04 — textos</a></aside>
        <div class="content-column">
          <section id="about" class="content-section about-section" aria-labelledby="about-title"><p class="section-number">01</p><div><h2 id="about-title">Um pouco sobre o caminho</h2><p class="lead">Comecei pelo curso técnico integrado ao ensino médio, na área de informática. Foi ali que o computador deixou de ser só uma ferramenta e virou um lugar para investigar.</p><p>Hoje curso Sistemas de Informação no IFSP — Campus Votuporanga e trabalho como Software Developer Junior na Lumiun. Gosto de entender como as peças se conectam: do código e dos dados às redes, aos sistemas operacionais e à infraestrutura.</p></div></section>

          <section id="work" class="content-section work-section" aria-labelledby="work-title"><p class="section-number">02</p><article class="work-entry"><div class="entry-meta"><span>desde 13.02.2025</span><span class="entry-rule" aria-hidden="true"></span><span>atual</span></div><h2 id="work-title">Software Developer Junior</h2><p class="company">Lumiun <span>·</span> ecossistema Lumiun DNS</p><p>Trabalho no desenvolvimento e na manutenção de sistemas, APIs e componentes relacionados ao produto. No dia a dia, transito principalmente pelo backend e por sistemas ligados a DNS e infraestrutura.</p><p class="tech-line"><span>no trabalho</span> PHP · Laravel · Go · Lua · MySQL · PostgreSQL · Redis · ClickHouse · RabbitMQ · Docker · JavaScript · Vue · Livewire</p></article></section>

          <section id="formation" class="content-section formation-section" aria-labelledby="formation-title"><p class="section-number">03</p><div><h2 id="formation-title">Formação</h2><div class="education-list"><article class="education-item"><p class="education-period">base</p><div><h3>Curso técnico integrado ao ensino médio</h3><p>Área de informática e desenvolvimento.</p></div></article><article class="education-item current-study"><p class="education-period">em andamento</p><div><h3>Sistemas de Informação</h3><p>IFSP — Campus Votuporanga</p></div></article></div></div></section>

          <section id="writing" class="content-section links-section" aria-labelledby="writing-title"><p class="section-number">04</p><div><h2 id="writing-title">Writing</h2><p>Escrevo para organizar o que aprendo — sobre desenvolvimento, tecnologia e as perguntas que aparecem enquanto um software é construído.</p><a class="text-link" href="https://dev.to/svitorz" target="_blank" rel="noreferrer">Ler no DEV Community <span aria-hidden="true">↗</span></a></div></section>
          <section class="content-section github-section" aria-labelledby="github-title"><div class="github-mark" aria-hidden="true">↳</div><div><h2 id="github-title">Código público</h2><p>Um registro aberto de coisas que estou estudando, testando e construindo no caminho.</p><a class="text-link" href="https://github.com/svitorz" target="_blank" rel="noreferrer">github.com/svitorz <span aria-hidden="true">↗</span></a></div></section>
          <aside class="interests" aria-label="Interesses pessoais"><span>fora do código</span><p>Música, cinema, jogos, basquete — e outras coisas que me lembram que uma vida boa também acontece longe da tela.</p></aside>
        </div>
      </div>
    </main>

    <footer class="site-footer"><span>Vitor Souza</span><address><a href="https://github.com/svitorz" target="_blank" rel="noreferrer">GitHub</a><a href="https://dev.to/svitorz" target="_blank" rel="noreferrer">DEV.to</a></address><span>© {{ currentYear }}</span></footer>
  </div>
</template>
