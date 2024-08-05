<template>
    <div class="back-part-block"></div>
    <div class="cart-block">
        <h1 class="title">Корзина</h1>
        <CartList />
        <MakingOrder />
    </div>
</template>

<script setup>
import CartList from './CartList.vue';
import MakingOrder from './MakingOrder.vue';
</script>

<style scoped>
.back-part-block {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: #00000093;
    z-index: 1;
}

.cart-block {
    position: fixed;
    top: 0;
    right: 0;
    z-index: 1;
    background-color: white;
    width: 380px;
    height: 100%;
    padding: 20px;
    overflow-y: auto;
}

.title {
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 30px;
}


</style>