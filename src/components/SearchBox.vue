<script setup>
import { ref, nextTick } from "vue";

const query = ref("");
const loading = ref(false);
const inputRef = ref(null);

const emit = defineEmits(["results"]);

const autoResize = async () => {
  await nextTick();

  if (!inputRef.value) return;

  inputRef.value.style.height = "auto";
  inputRef.value.style.height = inputRef.value.scrollHeight + "px";
};

const search = async () => {
  if (!query.value.trim()) return;

  loading.value = true;

  try {
    const response = await fetch(`${import.meta.env.VITE_API_URL}/search`, {
      method: "POST",

      headers: {
        "Content-Type": "application/json",
      },

      body: JSON.stringify({
        query: query.value,
      }),
    });

    const data = await response.json();

    emit("results", data);
  } catch (err) {
    console.error(err);
  } finally {
    loading.value = false;
  }
};

const handleEnter = (e) => {
  if (!e.shiftKey) {
    search();
  }
};

autoResize();
</script>

<template>
  <div class="search-wrapper">
    <div class="search-card">
      <div class="search-row">
        <textarea
          class="search-input"
          ref="inputRef"
          v-model="query"
          rows="1"
          @input="autoResize"
          @keydown.enter.prevent="handleEnter"
          placeholder="Ej: apartamento con 3 habitaciones en Guatemala menos de $200,000"
        />

        <button
          class="search-btn"
          @click="search"
          :disabled="loading || !query.trim()"
        >
          {{ loading ? "Buscando..." : "Buscar" }}
        </button>
      </div>
    </div>
  </div>
</template>
