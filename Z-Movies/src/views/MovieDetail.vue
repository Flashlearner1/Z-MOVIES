<template>
  <div class="movie-details">

    <div class="image">
      <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
    </div>

    <div class="info">
      <h2>{{movie.Title}}</h2>
      <p>{{ movie.Year }} <span>{{ movie.Runtime }}</span> </p>
      <p> {{ movie.Genre }}</p>
      <p class="imdb"> <img src="https://w7.pngwing.com/pngs/781/503/png-transparent-imdb-2016-hd-logo-thumbnail.png" alt="">{{ movie.imdbRating }}</p>
       <button class="Add"><a href="">Add to Wishlist</a></button>
       <p class="plot">{{ movie.Plot }}</p>
      <p class="direct">Directed By  <span>{{ movie.Director }}</span></p>
      <p class="write">Written By  <span>{{ movie.Writer }}</span></p>
      <p class="write">Actors  <span>{{ movie.Actors }}</span></p>
      
    </div>
    
  </div>
</template>

<script>
import { ref, onBeforeMount } from 'vue';
import { useRoute } from 'vue-router';
import env from '@/env.js';

export default {
  setup () {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
        .then(response => response.json())
        .then(data => {
          movie.value = data;
        });
    });

    return {
      movie
    }
  }
}
</script>

<style>

  .movie-details {
  padding: 16px;
  display: flex;
  padding-top: 60px;
  background: black;
  }

  .movie-details h2 {
  color: #FFF;
  font-size: 28px;
  font-weight: 600;
  margin-bottom: 16px;

  }

  .movie-details .featured-img {
    display: block;
    max-width: 400px;
    margin-bottom: 16px;
    margin-left: 40px;
  }

  .movie-details p {
    color: #fff;
    font-size: 18px;
    line-height: 1.4;
  }
  .info{
    margin-left: 50px;
  }
  .info .imdb{
    display: flex;
    align-items: center;
  }
  .info img{
    width: 35px;
    margin-right: 1px;
  }
  .Add{
    padding: 10px 30px 10px 30px;
    border-radius: 5px;
    margin-top: 30px;
  }
  .Add:hover{
    transition: .4s;
    background: red;
    transform: translateY(5px);
  }
  .Add a{
    color: black;
    font-size: 15px;
    font-weight: 800;
    text-decoration: none;
  }
  .plot{
    margin-top: 30px;
  }
  .direct{
    margin-top: 60px;
  }
  .direct span{
    margin-left: 50px;
  }
  .write{
    margin-top: 2px;
  }
  .write span{
    margin-left: 50px;
  }

</style>
