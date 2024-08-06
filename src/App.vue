<template>
    <!-- <Drawer /> -->
    <div class="main-block">
        <Header />
        <Content :items="items" />
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

import Header from './components/Header.vue'
import Content from './components/Content.vue';
import Drawer from './components/Cart/Drawer.vue';
import axios from 'axios';

const items = ref([])

onMounted(async () => {
    try {
        const {data} = await axios.get('https://604781a0efa572c1.mokky.dev/items?limit=12')
        const elements = data.items
        items.value = elements
    } catch {
        console.log('Данные не смогли прийти');
    }
})

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