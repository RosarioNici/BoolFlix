<template>
    <div>
            <div class="container-fluid" > 
                <div class="card mx-2 my-2">
                    <div class="img-hover">
                        <img class="img-fluid poster" :src="imgPath(film.poster_path)" alt="">
                    </div>
                    <div class="text p-3">
                        <ul class="list-unstyled"><h3>{{film.title}}</h3>
                            <li class="py-1"><h6>Titolo Originale: </h6>{{film.original_title}}</li>
                            <li class="py-1">Lingua: <img class="flag-size"  :src="addFlag(film.original_language)"></li>
                            <li class="py-1"><h5>Voto: </h5> <font-awesome-icon v-for="star in stars" :key="star" :icon="[star <= addStars ? 'fa-solid': 'fa-regular', 'fa-star']" />{{addStrars}}</li>
                            <li class="py-1"><h4>Trama: </h4><p>{{film.overview}}</p></li>
                        </ul> 
                     </div>
                </div>
                
            </div>
    </div>
</template>

<script>




export default {
    name: 'moviesComponent'  ,
    data(){
       return {stars: 5 }
    },
    props:{
    film:Object
   },
   computed:{
    addStars(){
          return Math.ceil(this.film.vote_average / 2)
    }
   },
   methods:{
    imgPath(codeImg){
        return `https://image.tmdb.org/t/p/w500/${codeImg}`
             
    },
    addFlag(flag){
        return `assets/1x1/${flag}.svg`
    },

    
        }}
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
    width: 400px;
  }
  .poster{
    border-radius: 10px;
    height: 600px;
  }
  p{
    font-size: small;
  }

</style>