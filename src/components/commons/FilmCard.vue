<template>
  <div class="card">
    <img
      class="poster"
      :src="'https://image.tmdb.org/t/p/original/' + info.poster_path"
      alt=""
    />
    <h3 v-if="info.title">{{ info.title }}</h3>
    <h3 v-else>{{ info.name }}</h3>
    <p>
      <img
        class="flag"
        :src="
          existingFlag(info.original_language)
            ? require(`../../assets/flags/${info.original_language}.png`)
            : null
        "
      />
    </p>
    <span v-if="info.vote_average <= 0"></span>
    <span v-else>
      <i v-for="index in addStar(info.vote_average)" :key="index">
        <span class="icon-color fas fa-star" style="color: gold"></span
      ></i>
    </span>
  </div>
</template>

<script>
export default {
  name: "FilmCard.vue",
  props: {
    info: Object,
  },
  data() {
    return {
      flags: ["en", "it", "de", "fr", "ja"],
    }
  },
  methods: {
    existingFlag(lang) {
      return this.flags.includes(lang)
    },
    addStar(vote) {
      return Math.round(vote / 2)
    },
  },
  computed: {
    vote() {
      return Math.ceil(this.info.vote_average / 2)
    },
  },
}
</script>

<style lang="scss" scoped></style>
