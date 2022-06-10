<template>
  <section class="film-section">
    <ul class="d-flex flex-wrap">
      <li
        class="card-box p-2"
        v-for="film in SelectedFilm.films"
        :key="film.id"
      >
        <img
          class="poster"
          :src="'https://image.tmdb.org/t/p/original/' + film.poster_path"
          alt=""
        />
        <h3>{{ film.title }}</h3>
        <p>
          <img
            class="flag"
            :src="
              existingFlag(film.original_language)
                ? require(`../../assets/flags/${film.original_language}.png`)
                : null
            "
          />
        </p>
        <p>{{ film.vote_average }}</p>
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
      flags: ["en", "it", "de", "fr"],
    }
  },
  methods: {
    existingFlag(lang) {
      return this.flags.includes(lang)
    },
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
