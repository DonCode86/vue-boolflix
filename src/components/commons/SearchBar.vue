<template>
<div class="search">
  <form @submit.prevent="SearchFilm()" class="d-flex">
  <input type="text" class="searchTerm" placeholder="Cerca il tuo film/serie tv" v-model="search">
    <button type="submit" class="searchButton"><i class="fa-solid fa-magnifying-glass"></i></button>
  </form>
</div>
</template>

<script>
  import axios from 'axios';
  import SelectedFilm from '@/shared/SelectedFilm';
  
export default {
    name: 'SearchBar',
    data() {
      return {
        search: '',
        SelectedFilm,
      }
    },
 methods:{
     SearchFilm(){
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '54ea321a9ac454295116f169f4a30268',
          query: this.search,
          language: 'it-IT'
        }
      }).then((response) => {
        SelectedFilm.films = response.data.results;
      }).catch((error) => {
        console.log(error);
      })
    },
  }
}
</script>

<style lang='scss' scoped>

.search {
  position: relative;
  display: flex;
}

.searchTerm {
  width: 100%;
  border: 3px solid rgba(255, 0, 0, 0.678);
  border-right: none;
  padding: 5px;
  border-radius: 5px 0 0 5px;
  outline: none;
  color: black;
}

.searchTerm:focus{
  color: #000;;

}

.searchButton {
  width: 40px;
  border: 1px solid rgba(255, 0, 0, 0.678);
  background: rgba(255, 0, 0, 0.678);
  text-align: center;
  color: #fff;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
  font-size: 20px;
}

.wrap{
  width: 30%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>