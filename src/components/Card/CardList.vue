<template>
    <div class="cards">
        <Card 
        imageURL="/sneakers/sneakers-1.jpg" 
        title="Мужские Кроссовки Nike Blazer Mid Suede" 
        :price="12999"
        :isAdded="false" 
        :isFavorite="false" 
        />
        
    </div>
</template>

<script setup>
import Card from '../Card/CardItem.vue';

</script>

<style scoped>
.cards {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    justify-items: center;
    gap: 20px;
}
</style>