<template>
  <div id="app">
    <navbar-starwars @input-changed="getKeyword" ></navbar-starwars>
    <div class="container">
      <character-list :characters="characters" :search="search"></character-list>
    </div>
    <floatButton  @character-added="showCharacters"></floatButton>
  </div>
</template>

<script>
import navbarStarwars from "./components/navbarStarwars";
import floatButton from "./components/FloatButton";
import characterList from "./components/CharacterList";
export default {
  name: "App",
  components: {
    navbarStarwars,
    floatButton,
    characterList
  },
  data(){
    return{
      characters: [],
      search: ""
    }
  },
  methods:{
    showCharacters(payload){
      this.characters = payload;
    },
    getKeyword(key){
      this.search = key;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  height:100vh;
  background: #ffffff;
  position: relative;
}
</style>
