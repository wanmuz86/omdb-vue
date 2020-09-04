<template>
  <div id="app">
    <div>
  <h1>My Movie app</h1>
  <input type="text" name="search"/>
  <button>Search</button>
  </div>
  <div>
    <h2>Results</h2>
    <div id="section" >
      <div v-for="film in films" :key="film.imdbID" v-on:click="selectFilm ">
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
selectFilm:function(event){
console.log(event)
  this.selectedFilm = {
      "Title": "Tenet",
      "Year": "2020",
      "imdbID": "tt6723592",
      "Type": "movie",
      "Poster": "https://m.media-amazon.com/images/M/MV5BYzg0NGM2NjAtNmIxOC00MDJmLTg5ZmYtYzM0MTE4NWE2NzlhXkEyXkFqcGdeQXVyMTA4NjE0NjEy._V1_SX300.jpg"
}
}
  },
  data() {
    return {
      "selectedFilm":null,
      "films" : [
      {
      "Title": "Tenet",
      "Year": "2020",
      "imdbID": "tt6723592",
      "Type": "movie",
      "Poster": "https://m.media-amazon.com/images/M/MV5BYzg0NGM2NjAtNmIxOC00MDJmLTg5ZmYtYzM0MTE4NWE2NzlhXkEyXkFqcGdeQXVyMTA4NjE0NjEy._V1_SX300.jpg"
},
{
"Title": "Roma te tenet et amoR",
"Year": "2011",
"imdbID": "tt2069901",
"Type": "movie",
"Poster": "N/A"
},
{
"Title": "Dark Tenet",
"Year": "2014",
"imdbID": "tt2243233",
"Type": "movie",
"Poster": "https://m.media-amazon.com/images/M/MV5BNzdlNmIzNjMtYzMyNS00NjkwLWJkNjAtNjhlNzIyZTIyZDUwXkEyXkFqcGdeQXVyNDk3OTU1ODc@._V1_SX300.jpg"
},
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
