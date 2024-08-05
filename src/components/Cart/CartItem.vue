<template>
    <div class="cart-item">
        <img class="sneackers-photo" src="/sneakers/sneakers-12.jpg" alt="Sneakers">
        <div class="text-block">
            <h1 class="title">Мужские Кроссовки Nike Air Max 270</h1>
            <p class="price">12 999 руб.</p>
        </div>
        <img class="icon-close" src="/icons/close.svg" alt="">
    </div>
</template>

<script>
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