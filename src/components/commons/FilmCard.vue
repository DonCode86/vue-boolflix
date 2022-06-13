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
    <p>{{ vote }}</p>
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
  },
  computed: {
    vote() {
      return Math.ceil(this.info.vote_average / 2)
    },
  },
}
</script>

<style lang="scss" scoped></style>
