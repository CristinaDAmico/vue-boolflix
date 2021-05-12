<template>
  <div id="app">
    <Header @search="getData"/>

    <Content :movies="movieList" :series="tvList"/>
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Content from "@/components/Content.vue";

export default {
  name: 'App',
  components: {
    Header,
    Content,
  },
  data() {
    return {
      apiURL: 'https://api.themoviedb.org/3/search/',
      apiKey: 'e0950fba3a982ffbbb125676b0a11b25',
      movieList: [],
      tvList: [],
    }
  },
  methods: {
    getData(searchText) {
      console.log(searchText);

      if(searchText !== '') {

        const apiParams = {
            api_key: this.apiKey,
            query: searchText,
            language: 'it-IT'
          };

        // chiamata api movie
        axios.get(this.apiURL + 'movie', {
          params: apiParams,
            
        }).then(res => {
            this.movieList = res.data.results;
        });
        // chiamata api serie tv
        axios.get(this.apiURL + 'tv', {
          params: apiParams,
        }).then(res => {
            this.tvList = res.data.results;
        })
      }
    }
  }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  height: 100vh;
  background-color:gray;
}

</style>
