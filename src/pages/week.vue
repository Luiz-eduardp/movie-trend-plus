<template>
  <q-page class="flex flex-center">
    <div class="movies-list">
      <div class="text-white text-uppercase text-h2 q-pa-md">
        Trending This week
      </div>
      <q-space />
      <div v-for="(movie, i) in movies" :key="i">
        <q-card class="movieCard q-pa-md">
          <q-card-section>
            <q-badge
              rounded
              color="primary"
              floating
              :label="movie.vote_average"
            />

            <q-img :src="'http://image.tmdb.org/t/p/w500/' + movie.poster_path">
              <div
                class="absolute-bottom text-subtitle2 text-center text-white"
              >
                {{ movie.title }} {{ movie.adult ? "+18" : "" }}
              </div>
            </q-img>
            <q-space />
            <q-separator />
            <q-card-section class="text-dark text-uppercase text-center">
              Release Date <b> {{ date(movie.release_date) }}</b>
              <br />
              Popularity <b>{{ movie.popularity }}</b> <br />Vote counts
              <b>{{ movie.vote_count }}</b>
            </q-card-section>
            <q-card-subtitle class="text-dark">
              {{ movie.overview }}
            </q-card-subtitle>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "PageIndex",
  created() {
    // Simple GET request using fetch
    fetch(
      "https://api.themoviedb.org/3/trending/movie/week?api_key=0d2b4096e6984acc803ea54a5acb0d4e"
    )
      .then((response) => response.json())
      .then((data) => (this.movies = data.results));
  },
  data() {
    return {
      movies: [],
    };
  },
  methods: {
    date(date) {
      return (
        date.split("-")[1] + "/" + date.split("-")[2] + "/" + date.split("-")[0]
      );
    },
  },
});
</script>
