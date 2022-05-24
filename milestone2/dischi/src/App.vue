<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="card" :key="index" v-for="(disco, index) in dischi">
          <div class="image">
            <img :src="disco.poster" alt="">
          </div>
          <div class="text">
            <h2>{{disco.title}}</h2>
            <div class="author">
              {{disco.author}}
            </div>
            <div class="year">
              {{disco.year}}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {

  data() {
    return{
      dischi: []
    }
  },

  name: 'App',
  components: {
    
  },

  mounted () {
    axios.get('http://localhost:8888/PHP/boolean/php-ajax-dischi/milestone2/php/')
        .then((oggetto) => {
          this.dischi = oggetto.data
          console.log(oggetto.data);
      });
  }
}
</script>

<style lang="scss">
@import './assets/scss/style.scss';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
 
}
</style>
