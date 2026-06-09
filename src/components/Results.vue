<script setup>
defineProps({
  results: {
    type: Array,
    default: () => [],
  },
});
</script>

<template>
  <div class="results">
    <div v-if="results.length" class="cards">
      <article class="card" v-for="item in results" :key="item.id">
        <div class="header">
          <span class="type">
            {{ item.tipo }}
          </span>

          <span class="price">
            Q {{ Number(item.precio).toLocaleString() }}
          </span>
        </div>

        <h2>
          {{ item.titulo }}
        </h2>

        <p class="desc">
          {{ item.descripcion }}
        </p>

        <div class="details">
          <span> {{ item.habitaciones }} habitaciones </span>

          <span> {{ item.banos }} baños </span>

          <span> {{ item.area_m2 }} m² </span>
        </div>

        <div class="footer">
          <span>
            {{ item.ciudad }}
          </span>

          <span>
            {{ item.ubicacion }}
          </span>
        </div>
      </article>
    </div>

    <div v-else class="empty">No hay resultados</div>
  </div>
</template>
