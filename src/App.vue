<script setup>
import { ref } from "vue";
import SearchBox from "./components/SearchBox.vue";
import Results from "./components/Results.vue";

const results = ref([]);

const updateResults = (data) => {
  results.value = data.properties || [];
};
</script>

<template>
  <header>
    <div class="logo">Prop<span>Search</span></div>
    <span class="header-tag">Búsqueda Inteligente</span>
  </header>

  <section class="hero">
    <h1 class="hero-title">
      Encuentra tu propiedad <em>ideal</em> en palabras simples
    </h1>
    <p class="hero-sub">Describe lo que buscas.</p>
  </section>

  <SearchBox @results="updateResults" />

  <Results :results="results" />

  <main></main>
</template>

<style scoped></style>
