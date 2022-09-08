<template>
  
  <div class="movie-detailss">

    <img class = "featured-img" :src="movie.Poster" alt="">
    <div class="m-detail">
      <h4>{{movie.Title}}</h4>
      <h5 >Released: {{movie. Released}}</h5>
      <p>{{movie.Plot}}</p>
    </div>
  </div>
</template>

<script>
  import {ref, onBeforeMount} from 'vue';
  import { useRoute } from 'vue-router';
 import env from "@/views/env.js";


export default {
  setup(){
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(()=>{

      fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
      .then((response)=>response.json())
      .then((data)=>{
        movie.value = data;
        console.log(data)
      });
    });

    return{
      movie
    }

  }


}
</script >


<style scoped>
 
 
.movie-detailss{
    display: flex;
    align-items: start;
    justify-content: start;
    width: 90%;
    margin-top: 60px;
   
  }

.m-detail{ 
 
  margin-left: 50px;
}

h4{
  color: #428883;
  font-size: 25px;
}

h5{
  margin-top: 15px;
  color: whitesmoke;
  font-size: 15px;
}

p{
  margin-top: 15px;
  line-height: 1.4;
}
.featured-img{
  margin-top: 15px;
  width:auto;
  
}

@media (max-width: 400px)
{
  .movie-detail{
    margin: 15px;
  }
.m-detail{
 
  margin-top: 15px;
}
p{
  line-height: 1.4;
}
.featured-img{
  margin-top: 15px;
  width:200px;
}

}
</style>