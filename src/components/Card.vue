<template>
  <div>
      <img v-if="details.poster_path" :src="`https://image.tmdb.org/t/p/w342${details.poster_path}`" alt="">
      <img v-else src="https://lh6.googleusercontent.com/proxy/oqZfItyVr9ljKfhHVg4MGubil6-uYpFbhxFQ5DrA5cLUH4KzNVq4Im2PxJxnVY07oWfBqBC6GKet7dT-m2CkuY8q7U0c6K9gkyoujcJUzR1lkrpxlC5mPIZIsm4Cfrsah4AwOGnYXUieuyR2Tfnn60k=s0-d" alt="">
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
            <li>
                <!-- {{ getStarVote(details.vote_average) }} -->
                <i 
                    v-for="i in getStarVote(details.vote_average)" 
                    :key="`full-${i}`" 
                    class="fas fa-star"
                ></i>
                <i 
                    v-for="i in 5 - getStarVote(details.vote_average)" 
                    :key="`empty-${i}`"  
                    class="far fa-star"
                ></i>
            </li>
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
        },
        getStarVote(vote) {
            return Math.ceil(vote / 2);
        }
    }
}
</script>

<style scoped lang="scss">
li img {
    width: 50px;
}

</style>