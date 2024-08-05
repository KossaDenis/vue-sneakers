<template>
    <div class="main-block">
        <Header />
        <div class="product-block">
            <h1 class="title">Все кроссовки</h1>
            <CardList />
        </div>
    </div>
</template>

<script setup>
import Header from '@/components/Header.vue'
import CardList from './components/CardList.vue';
</script>

<style scoped>
.main-block {
    background-color: white;
    width: 80%;
    margin: 30px auto;
    border-radius: 20px;
    box-shadow: 0px 10px 20px 0px #0000000A;
}

.product-block {
    padding: 35px 45px;
}

.title {
    margin-bottom: 30px;
    font-weight: 700;
    font-size: 32px;
}
</style>