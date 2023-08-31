<template>
    <header>
    <div class="Group1">
      <router-link to="/">
        <div class="logo">
          <span><a href="">FMovies</a></span>
        </div>
      </router-link>
      
          <div class="navigation">
            <ul>
              <li>
                <a href='/'>Home</a>
              </li>
              <li>
                <a href='/'>Series</a>
              </li>
              <li>
                <a href='/'>Movies</a>
              </li>
              <li>
                <a href='/'>Pages</a>
              </li>
              <li>
                <a href='/'>Pricing</a>
              </li>
              <li>
                <a href='/'>Contact</a>
              </li>
            </ul>
          </div>

      

      
      <div className='icon'>
        <form @submit.prevent="SearchMovies()" class="search-box">
          <input type="text" placeholder="Find Movies and TV" v-model="search" class="text"/>
          <input type="submit" value="Search" class="submit" />
          <i class='fas fa-bell'></i>
        <i class='fas fa-user'></i>
        
        <button>Subscribe Now</button>
        </form>

      </div>
      

    </div>

  </header>



  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0428251">
        <img src="https://cdn.dribbble.com/users/1032175/screenshots/9171102/media/5587beb47be46c1877862b3e7f812b75.png" alt="venom"  class="featured-img"  />
      </router-link>
    </div>
    



    <div class="movies-list">
      <div class="movie" v-for="movie in movies" :key="movie.imdbID">
        <router-link :to="'/movie/' + movie.imdbID" class="movie-link">
          <div class="product-image">
            <img :src="movie.Poster" alt="Movie Poster" />
            <div class="type">{{ movie.Type }}</div>
          </div>
          <div class="detail">
            <p class="year">{{ movie.Year }}</p>
            <h3>{{ movie.Title }}</h3>
          </div>
        </router-link>
      </div>
    </div>

  </div>
</template>

<script>
import { ref } from 'vue';
import env from '@/env.js'

export default {
  setup () {
    const search = ref("");
    const movies = ref([]);

    const SearchMovies = () => {
      if (search.value != "") {
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
          .then(response => response.json())
          .then(data => {
            movies.value = data.Search;
            search.value = "";
          });
      }
    }

    return {
      search,
      movies,
      SearchMovies
    }
  }
}
</script>

<style>

  .feature-card {
    position: relative;
   }

   .feature-card .featured-img {
      display: block;
      width: 100%;
      height: 700px;
      object-fit: center;
      position: relative;
      z-index: 0;
 }

  .feature-card .detail {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.6);
      padding: 16px;
      z-index: 1;
      display: flex;
      justify-content: space-between;
 }

 .feature-card h3 {
        color: #FFF;
        margin-bottom: 16px;
        font-size: 100px;
      }

  .feature-card p {
        color: #FFF;
        font-size: 40px;
  }

  .movies-list {
  display: flex;
  flex-wrap: wrap;
  margin: 0px 8px;
  color: black;
  }

 .movies-list .movie {
  max-width: 50%;
  flex: 1 1 1 50%;
  padding: 16px 8px;
 }
 .movies-list .movie-link {
    display: flex;
    flex-direction: column;
    height: 100%;

 }

 .movies-list .product-image {
  position: relative;
  display: block;
 }
 .movies-list img {
  display: block;
  width: 100%;
  height: 275px;
  object-fit: cover; }


 .movies-list .type {
  position: absolute;
  padding: 3px 6px;
  background-color: white;
  color: black;
  bottom: 2px;
  left: 0px;
  text-transform: capitalize;
  }

  .movies-list .detail {
  background-color: red;
  padding: 8px 4px;
  flex: 1 1 50%;
  border-radius: 0px 0px 8px 8px;
 } 
 .movies-list .year {
  color: white;
  font-size: 14px;
  list-style-type: none;
  text-decoration: none;
 }

  .movies-list h3 {
    color: white;
    font-weight: 600;
    font-size: 18px;
    text-decoration: none;
    list-style-type: none;
  }


  
  .search-box {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 16px;
    margin-left: 40px;
   }
   .search-box .text{
    padding: 10px 10px 10px 10px;
    border-radius: 16px 0px 16px 0px;
    width: 200px;
   }
   .search-box .text:focus{
    border-radius: 0px 16px 0px 16px;
   }
   .search-box .submit{
    padding: 10px 10px 10px 10px;
    margin-left: 1px;
    border-radius: 10px;
    background: red;
    color: white;
   }
   .search-box .submit:hover{
    background: black;
    transition: .4s;
    cursor: pointer;
   }
   .search-box button{
    margin-left: 0px;
   }

    * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
header{
  display: flex;
  justify-content: space-between;
}
.Group1{
  display: flex;
  justify-content: space-between;
}
.Group1 .logo{
  background: red;
  margin-left: 50px;
  border-radius: 2px;
}

.Group1 span {
  text-decoration: none;
  list-style-type: none;
  padding: 0px 10px 0px 10px;
  cursor: pointer;
  color: #fff;
  font-size: 20px;
}
.Group1 span a{
  color: #FFF;
  font-family:Georgia, 'Times New Roman', Times, serif ;
  font-weight: bold;
}
.navigation ul{
  display: flex;
  align-items: center;
  justify-content: space-between;
  list-style-type: none;
  margin-left: 80px;
}
.navigation ul li a{
  margin-left: 30px;
  text-decoration: none;
  color: #fff;
  font-size: 17px;
}
.navigation ul li a:hover{
  transition: .4s;
  color: red;
}

header{
  height: 10vh;
  line-height: 10vh;
  background-image: linear-gradient(to right bottom, rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0));
  color: #fff;
  position: fixed;
  z-index: 999;
  width: 100%;
}
header i {
  width: 40px;
  height: 40px;
  padding: 10px;
  text-align: center;
  border-radius: 50%;
  border: 2px solid #fff;
  margin: 0 10px;
  cursor: pointer;
}
header i:hover{
  transition: .4s;
  background: black;
}
.icon button {
  padding: 10px 25px 10px 25px;
  background: red;
  color: #fff;
  border-radius: 10px;
  margin-right: 50px;
}
.icon button:hover{
  transition: .4s;
  background: black;
  cursor: pointer;
}
.product-image img{
  width: 300px;
  height: 300px;
}


@media only screen and (max-width: 768px) {
  footer .container {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    grid-gap: 30px;
  }
}


</style>