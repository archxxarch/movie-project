<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import HeaderSection from '../components/section/HeaderSection.vue';
import FooterSection from '../components/section/FooterSection.vue';

const movies = ref([]);
const searchKeyword = ref('');

const fetchMovies = async (category) => {
  let url = 'https://api.themoviedb.org/3/movie/popular';

  switch (category) {
    case 'latest':
      url = 'https://api.themoviedb.org/3/movie/now_playing';
      break;
    case 'popular':
      url = 'https://api.themoviedb.org/3/movie/popular';
      break;
    case 'upcoming':
      url = 'https://api.themoviedb.org/3/movie/upcoming';
      break;
    case 'toprated':
      url = 'https://api.themoviedb.org/3/movie/top_rated';
      break;
  }

  try {
    const response = await axios.get(url, {
      params: {
        api_key: 'dcd0c80b9f7a0ed8c8384ea145bcc88b',
        language: "ko_KR",
        page: '1'
      }
    });
    // console.log(response)
    movies.value = response.data.results;

  } catch (err) {
    console.log(err)
  }
}

const searchMovies = async () => {
  if (!searchKeyword.value) {
    await fetchMovies('latest');
    return;
  }

  try {
    const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: 'dcd0c80b9f7a0ed8c8384ea145bcc88b',
        language: "ko_KR",
        query: searchKeyword.value,
      }
    });
    movies.value = response.data.results;
  } catch (err) {
    console.log(err);
  }
};

onMounted(async () => {
  await fetchMovies('latest');
});

</script>

<template>
  <HeaderSection />
  <main id="main" role="main">
    <div class="container">
      <div class="movie__inner">
        <section class="movie__search">
          <h2 class="blind">검색하기</h2>
          <input type="search" v-model="searchKeyword" placeholder="Search" @keyup.enter="searchMovies">
          <button type="submit" @click="searchMovies">GO</button>
        </section>
        <div class="movie__tag">
          <ul>
            <li><a href="#" @click="fetchMovies('latest')">RECENT</a></li>
            <li><a href="#" @click="fetchMovies('popular')">POPULAR</a></li>
            <li><a href="#" @click="fetchMovies('upcoming')">UPCOMING</a></li>
            <li><a href="#" @click="fetchMovies('toprated')">TOP RATED</a></li>
          </ul>
        </div>
        <section class="movie__cont">
          <h2 class="blind">영화</h2>
          <div class="movie play__icon" v-for="movie in movies" :key="movie.id">
            <a :href="'/detail/' + movie.id">
              <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" :alt="movie.title">
            </a>
          </div>
        </section>
      </div>
    </div>
  </main>

  <FooterSection />
</template>

<script>
import HeaderSection from '../components/section/HeaderSection.vue';
import FooterSection from '../components/section/FooterSection.vue';

import MovieSearch from "@/components/contents/MovieSearch.vue"
import MovieTag from "@/components/contents/MovieTag.vue"
import MovieCont from "@/components/contents/MovieCont.vue"

export default {
  name: "Movie Homepage",
  components: {
    HeaderSection,
    FooterSection,
    MovieSearch,
    MovieTag,
    MovieCont,
  },
  data() {
    return {
      movies: [],
    }
  },
  methods: {
    async search(query) {
      try {
        const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=dcd0c80b9f7a0ed8c8384ea145bcc88b&&language:ko-KR&query=${query}`)
        const results = await response.json();
        console.log(result);
      } catch (error) {
        console.log(error)
      }
    },
    async tags(query) {
      try {
        const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=dcd0c80b9f7a0ed8c8384ea145bcc88b&&language:ko-KR&query=${query}`)
        const results = await response.json();
        console.log(result);
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>

<style lang="scss">
.movie__search {
  margin: 20px 0;
  position: relative;

  input {
    // border: 1px solid #fff;
    padding: 1rem;
    width: 100%;
    border-radius: 20px;
    background-color: #555967;

  }

  button {
    position: absolute;
    right: 6px;
    top: 6px;
    width: 40px;
    height: 40px;
    background-color: #fff;
    color: #11131D;
    border-radius: 100px;
  }
}

.movie__tag {

  ul {
    display: flex;

    align-items: center;
    justify-content: center;
  }

  li {

    a {

      border: 1px solid #050608;
      color: #fff;
      border-radius: 10px;
      display: inline-block;
      padding: 0.5rem 2.5rem;
      margin-bottom: 20px;
      margin-right: 10px;
      margin-top: 20px;
      background-color: #2D2F3B;

      &:hover {
        background-color: #ffffff;
        color: #050608;
        transition: all 0.3s;
      }
    }
  }
}

.movie__cont {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;


  .movie {
    width: 24%;
    margin-bottom: 1.5%;
    background-color: #ccc;
  }
}
</style>
