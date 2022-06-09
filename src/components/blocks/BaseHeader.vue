<template>
  <header class="d-flex align-items-center">
    <div class="header-container container d-flex p-3 align-items-center justify-content-between">
        <div class="row">
            <img src="..\src\img\netflix-logo.png" alt="">
        </div>
    <SearchBar/>
    </div>
  </header>
</template>

<script>
import SearchBar from '../commons/SearchBar.vue';
export default {
    name: 'BaseHeader',
    components: {
        SearchBar,
    }
}
</script>

<style lang='scss' scoped>
header {
    background-color: rgb(0, 0, 0);

    img {
        height: 3rem;
        width: 13rem;
    }
}
</style>