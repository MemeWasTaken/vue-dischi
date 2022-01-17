<template>

    <div class="col">
        <div class="container-card d-flex flex-column align-items-center pt-3 pb-3 mb-4">
            <img
                :src="image"
                :alt="imageAlt">
            <h4 class="text-white text-card pt-3">{{ albumName }}</h4>
            <h5 class="text-card gray-subtitle pt-3">{{ albumArtist }}</h5>
            <h6 class="text-card gray-subtitle">{{ albumYear }}</h6>
        </div>
        </div>

</template>

<script>
export default {
    name: 'Card',
    props: {
        image: {
            type: String,
            required: true,
        },
        imageAlt: {
            type: String,
            required: true,
        },
        albumName: {
            type: String,
            required: true,
        },
        albumArtist: {
            type: String,
            required: true,
        },
        albumYear: {
            type: String,
            required: true,
        },
  },
}
</script>

<style lang="scss" scoped>
.col {

    .container-card {
        background-color: #2E3A46;
        width: 200px;
        height: 360px;
    
        img {
            width: 160px;
            height: 160px;
        }
        h4 {
            text-transform: uppercase;
            text-align: center;
        }
        .gray-subtitle {
            color: #808080;
        }
        .text-card {
            max-width: 180px;
            display: inline-block;
        }
    }
}
</style>