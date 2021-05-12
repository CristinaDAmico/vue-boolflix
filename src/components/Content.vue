<template>
  <main>
    <section class="movies">
      <h2>Movies</h2>
      <div>
          <Card 
            v-for="movie in movies" 
            :key="movie.id"
            :details="movie"
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
  }
}
</script>

<style lang="scss" scoped>

</style>