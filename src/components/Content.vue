<template>
  <main class="container">

    <section v-show="movies.length" class="movies">
      <h2>Movies</h2>
      <div>
          <Card 
            v-for="movie in movies" 
            :key="movie.id"
            :details="movie"
          />
      </div>
    </section>

    <section v-show="series.length" class="movies">
      <h2>Serie TV</h2>
      <div>
          <Card 
            v-for="serie in series" 
            :key="serie.id"
            :details="serie"
          />
      </div>
    </section>

  </main>
</template>

<script>
import Card from "@/components/Card.vue";

export default {
  name: 'Content',
  components: {
    Card
  },
  props: {
    movies: Array,
    series: Array,
  }
}
</script>

<style lang="scss" scoped>
h2 {
  color: #dc1a28;
  margin: 2rem 0;
}





</style>