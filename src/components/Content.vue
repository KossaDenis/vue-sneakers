<template>
    <div class="product-block">
        <div v-if="!loading" class="content-block">
            <h1 class="title">Все кроссовки</h1>
            <div class="select-search-block">
                <MySelect @change="$emit('sort', $event.target.value)">
                    <option value="default">По стандарту</option>
                    <option value='name'>По названию</option>
                    <option value='priceAscending'>По цене (дешевые)</option>
                    <option value='priceDescending'>По цене (дорогие)</option>
                </MySelect>
                <div class="search-block">
                    <MyInput @input="$emit('search', valueInput)" v-model="valueInput" type="text"
                        placeholder="Поиск..." />
                    <img class="icon-search" src="/public/icons/search.svg" alt="">
                </div>
            </div>
        </div>
        <div v-else>
            <MyLoading />
        </div>
        <CardList v-if="items.length" :items="items" />
        <div v-else-if="!loading" class="empty-state">
            <img src="/public/icons/sad-emoji.png" alt="">
            <h1>Ничего не найдино!</h1>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import CardList from './Card/CardList.vue';
import MyLoading from '../assets/UI/MyLoading.vue'
import MySelect from '@/assets/UI/MySelect.vue';
import MyInput from '@/assets/UI/MyInput.vue';

defineProps({
    items: Array,
    loading: Boolean
})

const valueInput = ref('');

</script>

<style scoped>
.product-block {
    padding: 35px 45px;
}

.content-block {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 50px;
}

.title {
    font-weight: 700;
    font-size: 32px;
}

.select-search-block {
    display: flex;
    gap: 5px;
}

.search-block {
    position: relative;
}

.icon-search {
    position: absolute;
    top: 15px;
    left: 18px;
}

.empty-state {
    margin-top: 80px;
    text-align: center;
}
</style>