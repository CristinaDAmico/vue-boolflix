<template>
  <div>
      <ul>
          <li>{{ details.title }}</li>
          <li>{{ details.original_title }}</li>
          <li>{{ details.original_language }}</li>
          <li>{{ details.vote_average }}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        details: Object,
    }
}
</script>

<style scoped lang="scss">

</style>