<template>
    <header class="header">
        <div class="information">
            <img class="logo" src="/icons/logo.png" alt="Logo">
            <div class="title-block">
                <h2 class="title">VUE SNEAKERS</h2>
                <p class="paragraph">Магазин лучших кроссовок</p>
            </div>
        </div>
        <ul class="user-panel">
            <li class="element-panel">
                <img src="/icons/cart.svg" alt="Cart">
                <p class="p-element-panel"><b>1205 руб.</b></p>
            </li>
            <li class="element-panel">
                <img src="/icons/heart.svg" alt="Cart">
                <p class="p-element-panel">Закладки</p>
            </li>
            <li class="element-panel">
                <img src="/icons/profile.svg" alt="Cart">
                <p class="p-element-panel">Профиль</p>
            </li>
        </ul>
    </header>
</template>

<script>

</script>

<style scoped>
.header {
    display: flex;
    justify-content: space-between;
    border-bottom: 2px solid #EAEAEA;
    padding: 35px 45px;
}

.information {
    display: flex;
    align-items: center;
}

.logo {
    width: 50px;
}

.title-block {
    margin-left: 16px;
}

.title {
    font-size: 20px;
    font-weight: 700;
}

.paragraph {
    font-size: 14px;
    font-weight: 400;
    color: #9D9D9D;
}

.user-panel {
    list-style-type: none;
    display: flex;
    align-items: center;
}

.element-panel {
    display: flex;
    margin-left: 32px;
    align-items: center;
    cursor: pointer;
}

.element-panel:first-child {
    margin-left: 0;
}

.p-element-panel {
    margin-left: 10px;
    font-size: 14px;
    color: #5C5C5C;
    transition: .2s;
}

.element-panel:hover p {
    color: black;
}
</style>