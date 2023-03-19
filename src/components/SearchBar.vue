<template>
    <div v-if="photos.length" class="search-input-container">
        <label class="search-label">Search Photos (titles might contain spaces):</label>
        <SimpleTypeahead
            placeholder="Title of thumbnail to display"
            :items="Object.keys(photoUrlsByTitle)"
            :minInputLength="3"
            @selectItem="handleSelectFromTypeAhead"
        >
        </SimpleTypeahead>
    </div>
</template>

<script setup>
    import { ref, computed, defineEmits } from 'vue';
    import SimpleTypeahead from "vue3-simple-typeahead";

    const photos = ref([]);
    (async () => {
        await fetch("https://jsonplaceholder.typicode.com/photos")
            .then(response => response.json())
            .then(json => { photos.value = json });
    })();
    
    const photoUrlsByTitle = computed(() => {
        return (photos.value || []).reduce((accum, photoData) => {
            accum[photoData.title] = photoData.thumbnailUrl;
            return accum;
        }, {});
    });

    const emit = defineEmits(["photoTitleSelected"]);
    function handleSelectFromTypeAhead(selectedValue) {
        emit("photoTitleSelected", photoUrlsByTitle.value[selectedValue]);
    }
</script>

<style scoped>
*, *::before, *::after {
  box-sizing: border-box;
}

.search-input-container {
    display: flex;
    justify-content: center;
    margin: 0.75rem;
}

.search-input-container :deep(input) {
    font-size: 1.125rem;
}

:deep(.simple-typeahead-list) {
    background-color: #BBEFFF;
    padding: 0.25rem;
    cursor: pointer;
}

.search-label {
    font-size: 1.125rem;
    margin-right: 0.5rem;
    margin-top: 0.25rem;
}
</style>