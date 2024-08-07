<template>
    <div class="cards">
        <transition-group>
            <Card v-for="item in items" :key="item.id" :imageURL="item.imageUrl" :title="item.title" :price="item.price"
                :isAdded="false" :isFavorite="false" />
        </transition-group>
    </div>
</template>

<script setup>
import Card from '../Card/CardItem.vue';
defineProps({
    items: Array
})


</script>

<style scoped>
.cards {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    justify-items: center;
    gap: 20px;
}
</style>