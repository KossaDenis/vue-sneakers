<template>
    <div class="product-block">
        <div class="content-block">
            <h1 class="title">Все кроссовки</h1>
            <div class="select-search-block">
                <select class="select">
                    <option>По названию</option>
                    <option>По цене (дешевые)</option>
                    <option>По цене (дорогие)</option>
                </select>
                <div class="search-block">
                    <input class="search" type="text" placeholder="Поиск...">
                    <img class="icon-search" src="/public/icons/search.svg" alt="">
                </div>
            </div>
        </div>
        <CardList :items="items" />
    </div>
</template>

<script setup>
import CardList from './Card/CardList.vue';
defineProps({
    items: Array
})
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

.select {
    padding: 10px 15px;
    border: 2px solid #EAEAEA;
    border-radius: 10px;
    outline: none;
}

.select:focus {
    border: 2px solid #b3b3b3;
}

.search {
    width: 250px;
    padding: 13px 15px 13px 46px;
    border: 2px solid #EAEAEA;
    border-radius: 10px;
    outline: none;
}

.search:focus {
    border: 2px solid #b3b3b3;
}
</style>