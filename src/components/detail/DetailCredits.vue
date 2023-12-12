<template>
    <div>
        <h3>캐스트</h3>
        <div>
            <div v-for="(movie, key) in movieCredits.cast" :key="key">
                <img :src="'https://image.tmdb.org/t/p/w185' + movieCredits.profile_path" alt="movie Profile" />
                <div>
                    <p>{{ movie.name }}</p>
                    <p>{{ movie.character }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        movieCredits: {
            type: Object,
            required: true,
        },
    },
};
</script>
  
<style lang="scss"></style>
  