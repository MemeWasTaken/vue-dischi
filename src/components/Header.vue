<template>
    <header>
        <div class="container-logo rounded-circle" >
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/2048px-Spotify_logo_without_text.svg.png" alt="">
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
}
</script>

<style lang="scss" scoped>
    header {
        background-color: #2E3A46;
        width: 100%;
        height: 10vh;
        padding: 0.6em;

        .container-logo {
            background-color: #191716;
            width: 70px;

            img {
                width: 70px;
                height: 70px;
            }
        }
    }
</style>