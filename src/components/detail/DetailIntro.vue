<template>
    <div class="intro"
        :style="{ backgroundImage: 'url(https://image.tmdb.org/t/p/original' + movieBasic.backdrop_path + ')' }">
        <div class="right">
            <div class="top">
                <p class="status">{{ movieBasic.status }}</p>
                <p class="tagline">{{ movieBasic.tagline }}</p>
            </div>

            <div class="middle">
                <h2 class="title">{{ movieBasic.title }}</h2>
                <p class="overview">{{ movieBasic.overview }}</p>
            </div>
            <div class="bottom">
                <p class="release_date">{{ movieBasic.release_date }}</p>
                <p class="runtime">{{ movieBasic.runtime }} 분</p>
                <p class="vote_average">{{ movieBasic.vote_average }} 점</p>
            </div>
            <!-- <div class="genre">
                <span v-for="genre in movieBasic.genres" :key="genre.id">
                    {{ genre.name }}</span>
            </div> -->

        </div>
        <div class="left">
            <div class="poster-container">
                <img :src="'https://image.tmdb.org/t/p/w500' + movieBasic.poster_path" alt="movie Poster" class="poster" />
            </div>
        </div>

    </div>
</template>
  
<script>
export default {
    props: {
        movieBasic: {
            type: Object,
            required: true,
        },
    },
};
</script>
  
<style lang="scss">
.intro {
    display: flex;
    padding: 3rem;

}

.right {
    width: 70%;
    background-color: #0000003e;
    backdrop-filter: blur(30px);
    padding: 3rem;
}

.left {}

.top {
    display: flex;
    padding-left: 1rem;
}

.status {
    background-color: #fff;
    border-radius: 100px;
    width: 100px;
    color: #000;
    text-align: center;
    font-size: 1rem;
    font-weight: 800;
    padding: 0.3rem;
}

.tagline {
    margin-left: 1rem;
    font-size: 1rem;
    margin-top: 0.3rem;
}

.middle {
    padding: 1rem;
}

.title {
    font-size: 3rem;
    font-weight: 800;
}

.bottom {
    display: flex;
    padding: 1rem;
}

.release_date,
.runtime,
.vote_average {
    background-color: #fff;
    border-radius: 80px;
    width: 130px;
    color: #000;
    text-align: center;
    font-size: 1.1rem;
    font-weight: 800;
    padding: 0.3rem;
    margin-right: 0.5rem;
}
</style>
  