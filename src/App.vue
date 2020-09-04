<template>
  <div id="app">
    <div>
      <h1>My Movie app</h1>
      <input type="text" name="search" v-model="searchTerm"/>
      <button v-on:click="buttonPressed">Search</button>
    </div>
    <div>
      <h2>Results</h2>
      <div id="section" >
        <div v-for="film in films" :key="film.imdbID" v-on:click="selectFilm(film)">
          <img v-bind:src="film.Poster">
          <h3>{{film.Title}}</h3>
          <p>{{film.Year}} - {{film.Type}}</p>
        </div> 

      </div>
    </div>
    <div id="more-info" v-if="selectedFilm">
      <img src="">
      <p>{{selectedFilm.Title}}</p>
      <p>{{selectedFilm.Year}}</p>
      <p>Robert Pattingson, Washington </p>
      <p>plot...</p>
    </div>
  </div>

</template>

<script>

  export default {
    name: 'App',

    methods:{
      buttonPressed:function(){
        fetch('http://www.omdbapi.com/?s='+this.searchTerm+'&apikey=87d10179') .then(response => response.json())
        .then(data => 
          this.films = data.Search
          );
      },

      selectFilm:function(film){
        this.selectedFilm = film
      }
    },
    data() {
      return {
        "searchTerm":"",
        "selectedFilm":null,
        "films" : [
        ]
      }
    }

  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
