<template>
  <section class="film-section">
    <h2>Film</h2>
    <ul class="d-flex flex-wrap">
      <li
        class="card-box p-2"
        v-for="film in SelectedFilm.films"
        :key="film.id"
      >
        <FilmCard :info="film" />
      </li>
    </ul>
    <h2>Serie TV</h2>
    <ul class="d-flex flex-wrap">
      <li class="card-box p-2" v-for="tv in SelectedFilm.tv" :key="tv.id">
        <FilmCard :info="tv" />
      </li>
    </ul>
  </section>
</template>

<script>
import SelectedFilm from "../../shared/SelectedFilm"
import FilmCard from "../commons/FilmCard.vue"
export default {
  name: "sectionFilm",
  components: {
    FilmCard,
  },
  props: {
    info: Object,
  },
  data() {
    return {
      SelectedFilm,
      flags: ["en", "it", "de", "fr", "ja"],
    }
  },
}
</script>

<style>
.poster {
  width: 18.75rem;
  height: 28.125rem;
}

.flag {
  width: 3rem;
}

li {
  list-style: none;
}

.card-box {
  width: 18.75rem;
  margin: 1.25rem;
}
</style>
