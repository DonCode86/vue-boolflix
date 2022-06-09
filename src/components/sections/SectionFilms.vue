<template>
  <section class="film-section">
    <ul>
      <li v-for="film in SelectedFilm.films" :key="film.id">{{film.title}}, {{film.original_title}}, {{film.original_language}}, {{film.vote_average}}   
      </li>
    </ul>
  </section>
</template>

<script>
import SelectedFilm from '../../shared/SelectedFilm'
export default {
 name: 'sectionFilm',
 data(){
    return{
       SelectedFilm,
    }
 }
}
</script>

<style>

</style>