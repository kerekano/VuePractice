<template>
  <nav>
    <div class="nav-wrapper">
      <form>
        <div class="input-field">
          <input id="search" type="search" @change="doSearching" v-model="search">
          <label class="label-icon" for="search"><i class="material-icons">search</i></label>
          <i class="material-icons">close</i>
        </div>
      </form>
    </div>
  </nav>
</template>

<script>
export default {
  data(){
    return{
      search: ""
    }
  },
  methods: {
    doSearching: function(){
      this.$emit("input-changed", this.search);
    }
  }
};
</script>
