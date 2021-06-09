<template>

  <header>
        <div id="logo">
           <router-link to="/">

            <h1><span>Vue</span>Movies</h1>

          </router-link>
        </div>
  </header>

  <main>
    <router-view/>
  </main>
  
</template>

<style>
  * {
    box-sizing: border-box;
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  body {
    margin: 0;
    padding: 0;
    background-color: #eafaf5;
    color: #202030;
  }

  header{
    background-color: #202030;
    padding: 5px;
  }

  header #logo {
    text-align: center;
  }

  a {
      color: inherit;
      text-decoration: none;
  }

  #logo span{
    font-weight: bolder;
    color: #55868C;
  }

  #logo h1{
    color: white;
    margin: 5px;
    transition: transform 250ms;
    display:inline-block;
  }

  #logo h1:hover {
    transform: scale(1.05, 1.05);
  }
  

</style>
