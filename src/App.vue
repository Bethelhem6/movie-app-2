<template>
 <header>
  <router-link to="/">
    <h1><span>Vue</span>Movies</h1>
  </router-link>

 </header>
  <router-view/>
</template>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'fira sans', sans-serif;

  }

  body{
    background: #35495E;
  }
a{
  text-decoration: none;
}

header{
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 16px;
  background: #2c3d4e;
  box-shadow: 0px 0px opx rgba(0,0,0,0.1);


}
h1{
  color: white;
  font-size: 28px;
}

span{
  color: #428883;
}


</style>
