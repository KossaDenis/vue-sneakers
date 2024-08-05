<template>
        <div class="cards">
            <Card />
        </div>
</template>

<script setup>
import Card from './Card.vue';

</script>

<style scoped>

.cards {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    justify-items: center;
    gap: 20px;
}
</style>