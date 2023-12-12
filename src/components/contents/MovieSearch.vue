<template>
    <section class="movie__search">
        <h2 class="blind">검색하기</h2>
        <input type="search" v-model="searchKeyword" placeholder="Search" @keyup.enter="searchMovies">
        <button type="submit" @click="searchMovies">GO</button>
    </section>
</template>

<script>
export default {

}
</script>