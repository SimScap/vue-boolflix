<template>
  <div>
    <Header @newSearch="updateMovieSearch"/>
    <Main :movies="movies" :series="series"/>
  </div>
</template>

<script>
import axios from "axios";
import Main from './components/Main.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Main,
    Header,
  },
  data : 
    function(){
      return {
        movies: [],
        series: [],
        moviesAndSeries : [],
        apiURL :'https://api.themoviedb.org/3/search/',
        apiKey : '?api_key=862b418e78bf66e4955745813391c00b&query=',
        movieSearch : '',
      }
    },
  methods: {
    updateMovieSearch(inputString){
    this.movieSearch = inputString;
    this.getMovies();
    this.getSeries();
    },
    getMovies(){
      axios
      .get(this.apiURL + 'movie' + this.apiKey + this.movieSearch)
      .then((response) =>{
        console.log(response.data.results);
        this.movies = response.data.results;
      })
      .catch ((error) =>{
        console.log(error);
      });
    },
    getSeries(){
      axios
      .get(this.apiURL + 'tv' + this.apiKey + this.movieSearch)
      .then((response) =>{
        console.log(response.data.results);
        this.series = response.data.results;
      })
      .catch ((error) =>{
        console.log(error);
      });
    }
  },
}
</script>

<style lang="scss">
@import '@/style/main-style.scss';
</style>


