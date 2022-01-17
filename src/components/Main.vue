<template>
    <main>
        <div class="cards-container pt-5">
                <div class="row row-cols-5 mx-auto">
                    <Card
                        v-for="(card, index) in records"
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
            })
            .catch((error) => {
                console.log(error);
            });
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