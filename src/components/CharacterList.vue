<template>
   <ul class="collection">
    <li class="collection-item avatar" 
    v-for="(character,index) in filteredList"
     :key="index">
      <img src="https://cmkt-image-prd.global.ssl.fastly.net/0.1.0/ps/1412243/1160/772/m1/fpnw/wm0/lawyer-avatar-flat-icon-01-.jpg?1467280299&s=d7eb6ecfdcefaea78ca2cef1143c9dde" alt="" class="circle">
      <span class="title">{{character.name}}<br>
        <button @click="onClick(show,character,index)" >Show More</button>
        <transition name="slide-fade">
          <p v-if="detail">
            <span v-if="characters[characters.indexOf(character)].name == name">
              Height: {{character.height}}<br>
              Mass: {{character.mass}}
            </span>
          </p>
        </transition>
      </span>
    </li>
  </ul>
</template>

<script>
export default {
  data(){
    return{
        show: false,
        name: "",
        detail: false
    }
  },
  props: {
    characters: Array,
    search: String
  },
  computed: {
    filteredList() {
      return this.characters.filter(character => {
        return character.name.toLowerCase().includes(this.search.toLowerCase());
      });
    }
  },
  methods: {
    onClick:function(status,name,index){
      status = !status;
      this.name = name.name;
      if(status) {
        if(this.characters[this.characters.indexOf(name)].name == name.name){
          this.detail = !this.detail;
        }
      }
      console.log(name.name);
      console.log(this.characters[this.characters.indexOf(name)].name);
    }
  }
}
</script>

<style>
.collection {
  border: none;
}
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
</style>
