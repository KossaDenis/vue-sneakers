<template>
    <!-- <Drawer /> -->
    <div class="main-block">
        <Header />
        <Content :loading="loading" :items="items" @search="searchElements" @sort="sortedElements" />

    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

import Header from './components/Header.vue'
import Content from './components/Content.vue';
import Drawer from './components/Cart/Drawer.vue';
import axios from 'axios';

const originalItems = ref([]);
const items = ref([]);
const searchText = ref('');
const sortMethod = ref('default');
const loading = ref(true);

onMounted(async () => {
    loading.value = true
    try {
        const { data } = await axios.get('https://604781a0efa572c1.mokky.dev/items?limit=12');
        const elements = data.items;
        originalItems.value = elements;
        items.value = elements;
    } catch {
        console.log('Данные не смогли прийти');
    } finally {
        loading.value = false
    }
})

const FiltersAndSorting = () => {
    let filteredItems = originalItems.value.filter(item =>
        item.title.toLowerCase().includes(searchText.value.toLowerCase().trim())
    );

    switch (sortMethod.value) {
        case 'default':
            filteredItems.sort((a, b) => a.id - b.id);
            break;
        case 'name':
            filteredItems.sort((a, b) => a.title.localeCompare(b.title));
            break;
        case 'priceAscending':
            filteredItems.sort((a, b) => a.price - b.price);
            break;
        case 'priceDescending':
            filteredItems.sort((a, b) => b.price - a.price);
            break;
        default:
            break;
    }

    items.value = filteredItems;
};

const searchElements = (text) => {
    searchText.value = text;
    FiltersAndSorting();
};

const sortedElements = (method) => {
    sortMethod.value = method;
    FiltersAndSorting();
};
</script>

<style scoped>
.main-block {
    background-color: white;
    width: 80%;
    margin: 30px auto;
    border-radius: 20px;
    box-shadow: 0px 10px 20px 0px #0000000A;

}
</style>