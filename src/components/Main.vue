<template>
    <main>
        <div class="cards-container pt-4">
            <div v-if="arrayFiltered">
                <div class="row">
                    <div class="col offset-10 pb-2">
                        <FilterGenre @filter="filteredRecords($event)" />
                    </div>
                </div>
                <div class="row row-cols-5 mx-auto">
                    <Card
                        v-for="(card, index) in arrayFiltered"
                        :key="index"
                        :image="card.poster"
                        :imageAlt="card.title"
                        :albumName="card.title"
                        :albumArtist="card.author"
                        :albumYear="card.year"
                    />
                </div>
            </div>
            <div v-else>
                <h1 class="text-white"> Loading... </h1>
            </div>
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue'
import FilterGenre from './FilterGenre.vue'

export default {
    name: "Main",
    components: {
        Card,
        FilterGenre,
    },
    data() {
    return {
      records: null,
      arrayFiltered: null,
    };
    },
    mounted() {
        setTimeout(() => {
            this.getCards();
        }, 4000);
    },
    methods: {
        getCards() {
        axios
            .get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((result) => {
                this.records = result.data.response;
                this.arrayFiltered = result.data.response;
            })
            .catch((error) => {
                console.log(error);
            });
        },
        filteredRecords (text) {
            this.arrayFiltered = this.records;

            if(text !== 'all') {
                this.arrayFiltered = this.arrayFiltered.filter(record => record.genre.toLowerCase() === text);
            } else {
                return this.arrayFiltered;
            }
            return this.arrayFiltered;
        },
    },
};

</script>

<style lang="scss" scoped>
    main {
        background-color: #1E2D3B;
        width: 100%;
        height: calc(100vh - 10vh);

        .cards-container {
            // border: 1px solid green;
            width: 70%;
            margin: 0 auto;
        }
    }
</style>