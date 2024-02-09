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
    setTitleFilter(term) {
      store.filter = term;
    },
    searchMovie(titleFilter) {
      const { baseUri, language, apikey } = api;

      const params = {
        query: store.filter,
        api_key: apikey,
        language
      }

      axios.get(`https://api.themoviedb.org/3/search/movie/api_key=05f372157df638c3b03248563b484a00&language=it-It&query=${store.filter}`)
        .then((res) => { store.movies = res.data.results })
        .catch((err) => {
          console.error(err)
        })
    }
  }
}
</script>

<template>
  <AppHeader @form-submit="searchMovie" />
</template>

<style scoped></style>
