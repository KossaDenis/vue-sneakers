<template>
    <div class="cart-item">
        <img class="sneackers-photo" :src="imageURL" alt="Sneakers">
        <div class="text-block">
            <h1 class="title">{{ title }}</h1>
            <p class="price">{{ price.toLocaleString('ru-RU') }} руб.</p>
        </div>
        <img @click="removeItem" class="icon-close" src="/icons/close.svg" alt="">
    </div>
</template>

<script setup>
const emit = defineEmits(['removeItemCart'])

const props = defineProps({
    id: Number,
    imageURL: String,
    title: String,
    price: Number,
})

const removeItem = () => {
    emit('removeItemCart', props.id)
}

</script>

<style scoped>
.cart-item {
    position: relative;
    display: flex;
    align-items: center;
    width: 100%;
    border: 2px solid #EAEAEA;
    border-radius: 20px;
    padding: 10px;
    margin-bottom: 15px;
}
.sneackers-photo {
    width: 100px;
}
.text-block{
    width: 150px;
    margin-left: 15px;
}
.title {
    font-size: 14px;
    font-weight: 400;
}
.price {
    font-size: 14px;
    font-weight: 700;
    margin-top: 8px;
}
.icon-close {
    position: absolute;
    bottom: 15px;
    right: 15px;
    cursor: pointer;
}
</style>