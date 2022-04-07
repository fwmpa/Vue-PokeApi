
<template>
  <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
  <h1>
    Requisições HTTP com Axios
  </h1>
  <div v-for="(pokemon, i) in pokemons" :key="i">
    <p>{{ pokemon.name }}</p>
  </div>
</template>

<script lang="ts">
  import { defineComponent, onMounted, ref } from "vue";
  import api from "@/services/api";

  export default defineComponent({
    setup() { 
      const pokemons = ref([]);

      const fetchPokemons = () => api.get("/pokemon?limit=20").then((response) => pokemons.value = response.data.results);

      onMounted(fetchPokemons);

      return { pokemons }
    }
  });
</script>