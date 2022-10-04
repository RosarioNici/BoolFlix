

<template>
  <div id="app">
    <header class="d-flex justify-content-between align-items-center">
      <div>
        <h1 class="title p-2">BOOLFLIX</h1>
      </div>
        <div class="header-container">
          <input type="text" v-model="call" @keyup.enter="searchfilms">
          <button @click="searchfilms">Cerca</button>
        </div>
    </header>
    <main>
        <h1 class="py-3">Films</h1>
        
            <div class="d-flex flex-wrap justify-content-around ">
              <moviesComponent class="col-md-3 col-sm-6 col-12" v-for="film in movies" :key="film.id" :film="film"/>
            </div>
        
        <h1 class="py-3">Serie TV</h1>
        <div class="d-flex flex-wrap justify-content-around">
          <seriesComponent class="col-md-3 col-sm-6 col-12" v-for="serie in series" :key="serie.id" :serie="serie"/>
        </div>
    </main>
  </div>
</template>

<script>
import moviesComponent from './components/moviesComponent.vue';
import seriesComponent from './components/seriesComponent.vue';
import axios from 'axios';
import { apiKey } from './env';

export default {
    name: "App",
    components: { moviesComponent, seriesComponent },
    data() {
        return {
            movies:[],
            series: [],
            call: "",
            
        };
    },
    mounted() {
        this.callApi(this.call);
    },
    methods: {
        searchfilms() {
            this.callApi(this.call);
        },
        callApi(textInput) {
          axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&query=${textInput}&language=it-IT`)
                .then((response) => {
                console.log(response);
                if (response.status === 200) {
                    this.movies = response.data.results;
                    console.log(this.movies);
                }
            })
                .catch((error) => {
                console.log(error);
            });
            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${apiKey}&language=it_IT&query=${textInput}`)
                .then((response) => {
                console.log(response);
                if (response.status === 200) {
                    this.series = response.data.results;
                    console.log(this.series);
                }
            })
                .catch((error) => {
                console.log(error);
            });

        },
    }}


</script>


<style lang="scss">
  @import '../node_modules/bootstrap';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
header{
  background-color: black;
  color: red; 
}
main{
  background-color: rgb(66, 65, 65);
}
.title{
  color: red;
}
h1{
  color: white;
}


</style>
