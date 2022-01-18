<template>
    <main>
        <div class="cards-container pt-5">
            <div class="row">
				<div class="col offset-10 pb-2">
                    <select v-model="selectionGenre" name="genre" id="genre" class="select" @change="filteredRecords">
                        <option value="all">All</option>
                        <option value="jazz">Jazz</option>
                        <option value="metal">Metal</option>
                        <option value="pop">Pop</option>
                        <option value="rock">Rock</option>
                    </select>
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
    </main>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue'

export default {
    name: "Main",
    components: {
        Card,
    },
    data() {
    return {
      records: null,
      selectionGenre: 'all',
      arrayFiltered: null,
    };
    },
    mounted() {
        this.getCards();
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
        filteredRecords() {
            this.arrayFiltered = this.records;

            if(this.selectionGenre !== 'all') {
                this.arrayFiltered = this.arrayFiltered.filter(record => record.genre.toLowerCase() === this.selectionGenre);
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