<template>
    <div class="making-order">
        <div class="making-order-content">
            <p class="text">Итого:</p>
            <p class="price">{{ totalSumCart.toLocaleString('ru-RU') }} руб.</p>
        </div>
        <button @click="makingOrder" class="order-button">Оформить заказ</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';

defineProps({
    totalSumCart: Number
})
const emptyArray = []

const stateOrder = ref(false)

const emit = defineEmits(['emptyArray', 'stateOrder']);

const makingOrder = () => {
    stateOrder.value = stateOrder.value === false ? true : false
    emit('emptyArray', emptyArray)
    emit('stateOrder', stateOrder)
}

</script>

<style scoped>
.making-order {
    margin-top: 30px;
}

.making-order-content {
    display: flex;
    justify-content: space-between;
}

.text {
    font-size: 16px;
    font-weight: 400;
}

.price {
    font-size: 16px;
    font-weight: 600;
}

.order-button {
    color: white;
    background-color: #9DD458;
    width: 100%;
    padding: 18px 30px;
    border: none;
    border-radius: 18px;
    cursor: pointer;
    transition: .3s;
    margin-top: 24px;
}

.order-button:hover {
    background-color: #89be47;
}
</style>