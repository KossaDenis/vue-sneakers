<template>
    <div class="card">
        <img class="icon-like" :src="isFavorite ? '/icons/like-2.svg' : '/icons/like-1.svg'" alt="Like 1">
        <img class="sneakers-photo" :src="imageURL" alt="Sneakers">
        <h2 class="title-card">{{ title }}</h2>
        <div class="block-price">
            <div>
                <p class="price-text">ЦЕНА:</p>
                <p class="price">{{ price }} руб.</p>
            </div>
            <div>
                <img class="icon-plus" :src="isAdded ? '/icons/checked.svg' : '/icons/plus.svg'" alt="Plus">
            </div>
        </div>
    </div>
</template>
<script setup>
defineProps({
    imageURL: String,
    title: String,
    price: Number,
    isAdded: Boolean,
    isFavorite: Boolean
}) 
</script>

<style scoped>
.card {
    position: relative;
    width: 210px;
    border: 2px solid #EAEAEA;
    border-radius: 40px;
    padding: 25px;
    transition: .2s;
    text-align: center;
    cursor: pointer;
    background-color: white;
}

.card:hover {
    transform: translateY(-10px);
    box-shadow: 0px 14px 30px 0px #0000000D;
}

.title-card {
    font-size: 14px;
    font-weight: 400;
    margin-bottom: 14px;
    text-align: left;
}

.sneakers-photo {
    width: 133px;
    margin-bottom: 14px;
}

.block-price {
    display: flex;
    justify-content: space-between;
    text-align: left;
}

.price-text {
    font-weight: 500;
    font-size: 11px;
    color: #BDBDBD;
    margin-bottom: 5px;
}

.price {
    font-size: 14px;
    font-weight: 700;
    color: black;
}

.icon-plus {
    cursor: pointer;
}

.icon-like {
    position: absolute;
    left: 23px;
    top: 16px;
    cursor: pointer;
}
</style>