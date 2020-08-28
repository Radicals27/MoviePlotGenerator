<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/image.png">
    <MovieIdea idea="Click the button for a new idea!"/>
  </div>
</template>

<script>
import MovieIdea from './components/Idea.vue'

export default {
  name: 'App',
  components: {
    MovieIdea
  }
}
</script>

<style>
 @import url('https://fonts.googleapis.com/css2?family=Karla&display=swap');
body {
    background-color: rgb(219, 219, 219);
}

img {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 30%;
}

#app {
    height: 10em;
    position: relative;
    font-family: Karla;
}

#app button {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 20%;
    margin-top: 1%;
    margin-bottom: 2%;

    background-color: #a3b0fa; 
    border: 2px solid #000000;
    color: rgb(0, 0, 0);
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    font-size: 2em;
}

#app button:hover {
    background-color: rgb(220, 230, 245);
}

#app h3 {
    font-size: 4em;

    margin: 0;
    text-align: center;
}

#app h4 {
    padding-top: 2%;
    font-size: 2.2em;
    margin: 0;
    text-align: center;
}
</style>
