<template>
    <div>
      <div class="container-fluid "> 
          <div class="card mx-2 my-2">
              <div class="img-hover">
                  <img class="img-fluid poster" :src="imgPath(serie.poster_path)" alt="">
              </div>    
              <div class="text p-3">
                  <ul class="list-unstyled "><h3>{{serie.name}}</h3>
                      <li class="py-1"><h5>Titolo Originale: </h5>{{serie.original_name}}</li>
                      <li class="py-1">Lingua: <img class="flag-size" :src="addFlag(serie.original_language)"></li>
                      <li class="py-1"><h5>Voto:</h5> <font-awesome-icon v-for="star in stars" :key="star" :icon="[star <= addStars ? 'fa-solid': 'fa-regular', 'fa-star']" />{{addStrars}}</li>
                      <li class="py-1">Trama: <p>{{serie.overview}}</p></li>

                      <button class="play"></button>
                  </ul> 
              </div>
               
          </div> 
         
      </div>
    </div>
  </template>
  
  <script>
  
  export default {
      name: 'seriesComponent',
      data(){
        return {stars: 5 }
      },
  props:{
      serie:Object
  }, 
  computed:{
    addStars(){
          return Math.ceil(this.serie.vote_average / 2)
    }
   },
  methods:{
      imgPath(codeImg){
          return `https://image.tmdb.org/t/p/w500/${codeImg}`
               
      },
      addFlag(flag){
        return `../assets/1x1/${flag}.svg`
    },
      addStrars(){
          return Math.ceil(this.serie.vote_average / 2)
    }
          }
  
  
  
  
  }
  </script>
  
  <style lang="scss" scoped>
    .img-hover{
    position: relative;
  }
  .text{
    color: white;;
  position: absolute;
  top: 5%;
  visibility: hidden;
  }
.card:hover{
    background-color: black;
}
.card:hover .img-hover{
    opacity: 0;
}
.card:hover .text{
   visibility: visible;
}
.flag-size{
    width: 20px;
    border-radius: 2px;
  }
  h5{
    display: inline;
  }
  .card{
    border-radius: 10px;
    height: 600px;
    width: 363px;
  }
  .poster{
    border-radius: 10px;
    height: 600px;
  }
  p{
    font-size: small;
  }
  
  </style>
  