<template>
    <div @click="handleClose" class="back-part-block"></div>
    <div class="cart-block">
        <h1 class="title">Корзина</h1>
        <div v-if="!stateOrder">
            <div v-if="itemsCart.length">
                <CartList :itemsCart="itemsCart" @removeItemCart="removeItem" />
                <MakingOrder :totalSumCart="totalSumCart" @emptyArray="emptyArray" @stateOrder="change" />
            </div>
            <div class="block-empty-cart" v-else>
                <img class="package-icon" src="/public/icons/package-icon.png" alt="">
                <h2 class="title-empty-cart">Корзина пустая</h2>
                <p class="paragraph-empty-cart">Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ.</p>
            </div>
        </div>
        <div class="block-order-success" v-else>
            <img class="order-success-icon" src="../../../public/icons/order-success-icon.png" alt="">
            <h2 class="title-order-success">Заказ оформлен!</h2>
            <p class="paragraph-order-success">Ваш заказ скоро будет передан курьерской доставке</p>
        </div>

    </div>
</template>

<script setup>
import { ref } from 'vue';
import CartList from './CartList.vue';
import MakingOrder from './MakingOrder.vue';

const props = defineProps({
    itemsCart: Array,
    totalSumCart: Number
})

const emit = defineEmits(['closeDrawer', 'removeItemCart', 'emptyArray']);

const stateOrder = ref(false)


const handleClose = () => {
    emit('closeDrawer');
};

const removeItem = (item) => {
    emit('removeItemCart', item)
}

const emptyArray = (array) => {
    emit('emptyArray', array)
}

const change = (state) => {
    stateOrder.value = state
}

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

.block-empty-cart {
    text-align: center;
    margin-top: 50%;
}

.package-icon {
    width: 120px;
}

.title-empty-cart {
    font-size: 22px;
    font-weight: 600;
    margin-top: 21px;
}

.paragraph-empty-cart {
    margin-top: 9px;
    font-size: 16px;
    font-weight: 400;
    color: #BDBDBD;
}

.title {
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 30px;
}

.block-order-success {
    text-align: center;
    margin-top: 50%;
}

.order-success-icon {
    width: 83px;
    margin-bottom: 30px;
}

.title-order-success {
    font-size: 22px;
    font-weight: 600;
    color: #87C20A;
    margin-bottom: 9px;
}

.paragraph-order-success {
    font-size: 16px;
    font-weight: 400;
    color: #BDBDBD;
}
</style>