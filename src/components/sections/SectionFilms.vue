<template>
  <section class="film-section">
    <ul>
      <li v-for="film in SelectedFilm.films" :key="film.id">
        <img
          :src="'https://image.tmdb.org/t/p/original/' + film.poster_path"
          alt=""
        />
        {{ film.title }}, {{ film.original_title }},
        {{ film.original_language }}, {{ film.vote_average }}
      </li>
    </ul>
  </section>
</template>

<script>
import SelectedFilm from "../../shared/SelectedFilm"
export default {
  name: "sectionFilm",
  data() {
    return {
      SelectedFilm,
    }
  },
}
</script>

<style>
img {
  width: 18.75rem;
}
</style>
