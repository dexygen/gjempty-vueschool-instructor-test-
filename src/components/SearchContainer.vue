<template>
    <SearchBar @photoTitleSelected="updateThumbnailSrc" />
    <div class="thumbnail-placeholder">
        <img ref="thumbnailRef" src="">
    </div>
</template>

<script setup>
import SearchBar from "./SearchBar.vue";
import { ref } from 'vue';

const thumbnailRef = ref(null);
function updateThumbnailSrc(thumbnailUrl) {
    thumbnailRef.value.src = thumbnailUrl;
}
</script>

<style scoped>
.thumbnail-placeholder {
    display: flex;
    justify-content: center;
}
</style>