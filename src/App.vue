<script>
import axios from "axios";
import { store } from "./data/store";
import { api } from "./data/index";
import AppHeader from './components/AppHeader.vue';
export default {
  name: "Boolflix",
  components: { AppHeader },
  data: () => ({ store }),
  methods: {

    searchMovie(titleFilter) {
      const { baseUri, language, apiKey } = api;

      const params = {
        query: store.searchText,
        api_key: apiKey,
        language
      }
      axios.get(`${baseUri}/search/movie`, { params })
        .then((res) => { store.movies = res.data.results })
        .catch((err) => {
          console.error(err)
        })
    }
  }
}
</script>

<template>
  <AppHeader @form-submit="searchMovie(titleFilter)" />
</template>

<style scoped></style>
