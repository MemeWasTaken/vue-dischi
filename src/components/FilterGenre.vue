<template>
    <select v-model="selectionGenre" name="genre" id="genre" class="select" @change="$emit('filter', selectionGenre)">
        <option value="all">All</option>
        <option value="jazz">Jazz</option>
        <option value="metal">Metal</option>
        <option value="pop">Pop</option>
        <option value="rock">Rock</option>
    </select>
</template>

<script>
export default {
    name: "FilterGenre",
    data() {
        return {
            selectionGenre: 'all',
        };
    },
}
</script>

<style>

</style>