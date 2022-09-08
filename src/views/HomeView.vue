<template>
  <div class="home">
 <div class="featured-card">
  <router-link to="/movie/tt11337862">

    <img class="featured-img" src= "https://m.media-amazon.com/images/M/MV5BODI0MzdhODAtNDMwNi00NGZlLTg1Y2YtN2M5ZGFmOThkZGM3XkEyXkFqcGdeQXVyMTkxNjUyNQ@@._V1_SX300.jpg" alt=" Friends: The Reunion" >

    <div class="detail">
      <h3>
        Friends: The Reunion
      </h3>
      <p>For the first time after seventeen years, and their last appearance on The Last One (2004), the final episode of the TV series, Friends (1994), Jennifer Aniston; Courteney Cox; Lisa Kudrow; Matt LeBlanc; Matthew Perry, and David Schwimmer, find themselves under the same roof for a reunion special. Hosted by James Corden, and produced by the show's co-creators, Marta Kauffman, David Crane, and Kevin Bright, the show's main cast feels at home in the original sets of Friends (1994), taking a trip down memory lane while sitting on Central Perk's couch. Brimming with emotion, laughter, and tears of joy, \"Friends: The Reunion\" sheds light on ambivalent endings, the casting process, and many more, as the main cast re-enacts older Friends episodes and meets with a plethora of celebrity guests, including Maggie Wheeler, the show's Janice Litman-Goralnik; Justin Bieber; Cindy Crawford; Cara Delevingne; Lady Gaga; David Beckham; Tom Selleck, and Nobel Peace Prize laureate, Malala Yousafzai.</p>
    </div>
  </router-link>
 </div>
 <form @submit.prevent="SearchMovies()" class="search-box">
  <input type="text" placeholder="What are you looking for?" v-model="search" class = "txt">
  <input type="submit" value="Search" class = "btn">
 </form>

 <div class="movie-list">
  <div class="movie" v-for="movie in movies" :key="movie.imdbID">
   <router-link :to="'/movie/' + movie.imdbID" class="movie-link">
    <div class="product-img">
      <img :src="movie.Poster" alt="Movie Poster">
      <div class="type">{{movie.Type}}</div>
    </div>
    <div class="detail-2">
      <p class="year">
        {{movie.year}}
      </p>
      <h3 class="title">{{movie.Title}}</h3>
    </div>
   </router-link>
  </div>
 </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { ref } from "vue";
import env from "@/views/env.js"

export default {
  setup(){

    const search =ref('');
    const movies = ref([]);

    const SearchMovies = ()=>{
      if(search.value != ''){
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
        .then(response=> response.json())
        .then(data=>{
          movies.value = data.Search;
          // search.value='';
          // console.log(data);
        })
      }

    }

    return{
      search,
      movies,
      SearchMovies
    }
  }
 
 
}
</script>

<style>
    
  .featured-card{
    position: relative;

  }
  .featured-img{
    display: block;
    width: 100%;
    height: 300px;
    object-fit: cover;
    position: relative;
    z-index: 0;


  }
  .detail{
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0,0,0,0.6);
    padding: 10px;
    z-index: 1;

  }
  h3{
    color: white;
    margin-bottom: 10px;
  }

  p{
    color: white;
  }

  .search-box{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 10px;

  }

  input{
    display: block;
    appearance: none;
    border: none;
    outline: none;
    background: none;

  }
.txt
{
  width: 100%;
  color: white;
  background: #496583;
  font-size: 28px;
  padding: 10px 10px;
  border-radius: 8px;
  margin-bottom: 15px;
  transition: 0.45;

} 

::placeholder{
  color: white;
}
:focus{
  box-shadow: 0px 3px 6px rgba(0,0,0,0.2);
}

.btn{
  width: 100%;
  max-width: 300px;
  background: #428883;
  color: white;
  padding: 10px;
  border-radius: 8px;
  font-size: 28px;
  text-transform: uppercase;
  transition: 0.4s;
}
.btn:active{
  background: #041819;
}

.movie-list{
  display: flex;
  flex-wrap: wrap;
  margin: 0px 0px;

}

.movie{
  max-width: 50%;
  flex: 1 1 50%;
  padding: 10px 10px;

}

.movie-link{
  display: flex;
  flex-direction: column;
  height: 100%;

}

.product-img{
  position: relative;
  display: block;
}
img{
  display: block;
  width: 100%;
  height: 270px;
  object-fit: cover;
}
.type{
  position: absolute;
  padding: 10px 10px;
  background:#428883;
  color: white;
  bottom: 10px;
  left: 0;
  text-transform: capitalize;

}
.detail-2{
  background: #0a2f2b;
  padding: 15px 8px;
  flex: 1 1 10px;
  border-radius: 0px 0px 0px 0px;

}

.year{
  color: #AAA;
  font-size: 14px;
}
.title{
  font-size: 10px;
  color: #fff;
}

@media (min-width: 600px){
   .featured-card{
    position: relative;
   
    
   
  }
  .featured-img{
    margin-left: 450px;
    display: block;
    align-items: center;
    width: 400px;
    height: 400px;
    object-fit: cover;
    position: relative;
    z-index: 0;


  }

  .detail{
    margin-right: 50px;
    margin-left: 50px;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0,0,0,0.6);
    padding: 20px;
    z-index: 1;
    
  }
  h3{
    color: white;
    margin-bottom: 10px;
  }

  p{
    color: white;
  }

  .search-box{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 10px;
    
  }

  input{
    display: block;
    appearance: none;
    border: none;
    outline: none;
    background: none;

  }
.txt
{
  width: 100%;
  color: white;
  background: #496583;
  font-size: 28px;
  padding: 10px 10px;
  border-radius: 8px;
  margin-bottom: 15px;
  transition: 0.45;

} 

::placeholder{
  color: white;
}
:focus{
  box-shadow: 0px 3px 6px rgba(0,0,0,0.2);
}

.btn{
  width: 100%;
  max-width: 300px;
  background: #428883;
  color: white;
  padding: 10px;
  border-radius: 8px;
  font-size: 28px;
  text-transform: uppercase;
  transition: 0.4s;
}
.btn:active{
  background: #041819;
}

.movie-list{
  display: flex;
  flex-wrap: wrap;
  margin: 10px 10px;

}

.movie{
  max-width: 50%;
  flex: 1 1 1 50%;
  padding: 10px 10px;

}

.movie-link{
  display: flex;
  flex-direction: column;
  height: auto;

}

.product-img{
  position: relative;
  display: block;
}
img{
  display: block;
  width: 100%;
  height: 270px;
  object-fit: cover;
}
.type{
  position: absolute;
  padding: 10px 30px 10px 30px;
  background:#428883;
  color: white;
  bottom: 10px;
  left: 0;
  text-transform: capitalize;

}
.detail-2{
  background: rgba(0,0,0,0.6);
  padding: 15px 8px;
  flex: 1 1 10px;
  border-radius: 0px 0px 0px 0px;

}

.year{
  color: #AAA;
  font-size: 20px;
}
.title{
  font-size: 15px;
  color: #fff;
}

}

</style>