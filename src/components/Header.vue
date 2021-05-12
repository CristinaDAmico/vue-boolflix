<template>
  <header class="top-bar">
      <a href="#">
        <img src="../assets/image/logo.png" alt="logo">
      </a>
      <div>
        <input type="text" placeholder="Search movie" v-model.trim="searchText">
        <button @click="$emit('search', searchText)">Search</button>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
      return {
        searchText: '',
      }
    }
}
</script>

<style lang="scss" scoped>
.top-bar {
  height: 80px;
  background-color: #000;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 50px;
  img {
    width: 150px;
  }
}

</style>