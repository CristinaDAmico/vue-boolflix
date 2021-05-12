<template>
  <div>
      <ul>
            <li>{{ details.title ? details.title : details.name }}</li>
            <li>{{ details.original_title ? details.original_title : details.original_name }}</li>
            <li>
                <img v-if="isFlag(details.original_language)" 
                    :src="require(`@/assets/image/${details.original_language}.png`)" 
                    :alt="details.original_language"
                >
                <span v-else>{{ details.original_language }}</span>
            </li>
            <li>{{ details.vote_average }}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        details: Object,
    },
    data() {
        return {
            flagsImg: ['it', 'en']
        }
    },
    methods: {
        isFlag(lang) {
            return this.flagsImg.includes(lang);
        }
    }
}
</script>

<style scoped lang="scss">
li img {
    width: 50px;
}

</style>