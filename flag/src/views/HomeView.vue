<script>
import { reactive } from "vue";
export default {
  data() {
    return {
      countries: reactive([]),
    };
  },
  async mounted() {
    try {
      const response = await fetch("https://restcountries.com/v3.1/all");
      const data = await response.json();

      this.countries = data;
    } catch (error) {
      console.error("Erreur lors de la récupération des données :", error);
    }
  },
};
</script>

<template>
  <main>
    <h1>Hello</h1>
    <div>
      <li v-for="country in countries" :key="country.name.common">
        <img :src="country.flags.svg" alt="Drapeau" />
        {{ country.name.common }}
      </li>
    </div>
  </main>
</template>
