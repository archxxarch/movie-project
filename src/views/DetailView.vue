<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1>AniMovie</h1>
                <nav>
                    <ul>
                        <li><a href="#">DISNEY Movie</a></li>
                        <li><a href="#">PIXAR Movie</a></li>
                        <li><a href="#">MARVEL Movie</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
    <main id="main">
        <DetailIntro v-if="movieBasic" :movieBasic="movieBasic" />
        <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" />
        <DetailReview v-if="movieReview" :movieReview="movieReview" />
        <DetailCredits v-if="movieCredits" :movieCredits="movieCredits" />
    </main>
</template>

<script>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import axios from 'axios';

import DetailIntro from "../components/detail/DetailIntro.vue"
import DetailInfo from "../components/detail/DetailInfo.vue"
import DetailReview from "../components/detail/DetailReview.vue"
import DetailCredits from "../components/detail/DetailCredits.vue"

export default {
    name: "MovieDetailPage",

    components: {
        DetailIntro,
        DetailInfo,
        DetailReview,
        DetailCredits
    },

    setup() {
        const movieBasic = ref(null);
        const movieInfo = ref(null);
        const movieReview = ref(null);
        const movieCredits = ref(null);

        const route = useRoute();

        onMounted(async () => {
            const movieId = route.params.movieId;
            const apiKey = import.meta.env.VITE_API_KEY;
            const language = "ko-KR";

            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieBasic.value = resMovieBasic.data;
                console.log(resMovieBasic.data)

                const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieInfo.value = resMovieInfo.data;

                const resMovieReview = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieReview.value = resMovieReview.data;

                const resMovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/credits?language=${language}&api_key=${apiKey}`);
                movieCredits.value = resMovieCredits.data;
                console.log(resMovieCredits.data)
            } catch (err) {
                console.log(err)
            }
        });

        return { movieBasic }
    }
}


</script>

<style lang="scss">
.header__inner {
    .header__nav {
        display: flex;
        justify-content: space-between;
        align-items: center;

        h1 {
            font-size: 23px;
            font-weight: 800;
            color: #fff;
            background-color: #2D2F3B;
            margin: 20px;
            border-radius: 20px;
            display: inline-block;
            padding: 10px;
        }

        nav {
            ul {
                display: flex;

                li {
                    margin: 1rem;
                    padding: 0.8rem;
                    border-radius: 10px;
                    color: #fff;
                    font-weight: 800;
                    font-size: 15px;

                    &:hover {
                        background-color: #3e4151;
                    }
                }
            }
        }

    }


}

.header__intro {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    position: relative;
    padding: 30px;
    background-color: #fff;

    &::before {
        content: '';
        width: 100%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background-color: #ffffff00;
        backdrop-filter: blur(40px);
        z-index: 1;
    }

    .container {
        display: flex;
        justify-content: space-between;
        position: relative;
        z-index: 10;


        .left {
            width: 350px;
        }

        .right {
            width: calc(100% - 400px);
            color: #fff;

            h2 {
                font-size: 30px;
                margin-bottom: 10px;
            }

            .desc {
                margin-bottom: 10px;

            }
        }
    }
}

.credits {
    display: flex;
    padding-top: 6.5rem;
}

.credits img {
    padding-left: 0.5rem;

}
</style>