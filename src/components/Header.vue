<template>
  <header class="top-bar">
    <div class="container">
      <a href="#">
        <img src="../assets/image/logo.png" alt="logo">
      </a>
      <div>
        <input type="text" placeholder="Search movie" v-model.trim="searchText">
        <button @click="$emit('search', searchText)">Search</button>
      </div>
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
  background-color: #000;
  .container {
    height: 80px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  img {
    width: 150px;
  }
  button {
    margin-left: 10px;
  }
}

</style>