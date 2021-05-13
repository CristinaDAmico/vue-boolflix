<template>
   
    <div class="box">
        <div class="copertina">
            <img v-if="details.poster_path" :src="`https://image.tmdb.org/t/p/w342${details.poster_path}`" alt="">
            <img class="no-post" v-else src="https://lh6.googleusercontent.com/proxy/oqZfItyVr9ljKfhHVg4MGubil6-uYpFbhxFQ5DrA5cLUH4KzNVq4Im2PxJxnVY07oWfBqBC6GKet7dT-m2CkuY8q7U0c6K9gkyoujcJUzR1lkrpxlC5mPIZIsm4Cfrsah4AwOGnYXUieuyR2Tfnn60k=s0-d" alt="">
        </div>
        <div class="info-film">
            <ul>
                <li><span>Titolo: </span>{{ details.title ? details.title : details.name }}</li>
                <li><span>Titolo originale: </span>{{ details.original_title ? details.original_title : details.original_name }}</li>
                <li>
                    <span>Lingua: </span>
                    <img v-if="isFlag(details.original_language)" 
                        :src="require(`@/assets/image/${details.original_language}.png`)" 
                        :alt="details.original_language"
                        class="bandiera"
                    >
                    <span v-else>{{ details.original_language }}</span>
                </li>
                <li>
                    <span>Voto: </span>
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
                <li><span>Overview: </span>{{details.overview}}</li>
            </ul>
        </div>
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
img{
    width: 100%;
    height: 100%;
}

.bandiera {
    width: 30px;
}

.box {
    width: 32%;
    margin-right: 1%;
    margin-bottom: 2rem;
    height: 520px;
    display: inline-block;
    position: relative;
    cursor: pointer;
}

.info-film,
.copertina {
    width: 100%;
    height: 100%;
}

.info-film {
    padding: 2rem 1rem;
    border: 3px solid #fff;
    position: absolute;
    top: 0;
    left: 0;
    color: #fff;
    background: #000;
    display: none;
}

.box:hover .info-film {
    display: block;
}

ul {
    list-style: none;
    li {
        margin-bottom: 10px;
    }

}

.info-film i {
    color: yellow;
}

span {
    font-weight: bold;
}

</style>