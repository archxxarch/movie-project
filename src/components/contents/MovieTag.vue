<template>
    <div class="movie__tag">
        <ul>
            <li><a href="#" @click="fetchMovies('latest')">RECENT</a></li>
            <li><a href="#" @click="fetchMovies('popular')">POPULAR</a></li>
            <li><a href="#" @click="fetchMovies('upcoming')">UPCOMING</a></li>
            <li><a href="#" @click="fetchMovies('toprated')">TOP RATED</a></li>

        </ul>
    </div>
</template>