<template>
    <!-- <Drawer /> -->
    <div class="main-block">
        <Header />
        <Content />
    </div>
</template>

<script setup>
import Header from './components/Header.vue'
import Content from './components/Content.vue';
import Drawer from './components/Cart/Drawer.vue';
</script>

<style scoped>
.main-block {
    background-color: white;
    width: 80%;
    margin: 30px auto;
    border-radius: 20px;
    box-shadow: 0px 10px 20px 0px #0000000A;

}
</style>