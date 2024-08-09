<template>
    <div class="cards">
        <transition-group>
            <Card v-for="item in items" :key="item.id" :imageURL="item.imageUrl" :title="item.title" :price="item.price"
                :itemId="item.id" :removeElement="removeElement" @itemPrice="totalSumCart" @newItem="newItemInCart"
                @isChecked="checkedState" />
        </transition-group>
    </div>
</template>

<script setup>
const emit = defineEmits(['totalSum', 'newItem', 'isChecked'])

import Card from '../Card/CardItem.vue';
const props = defineProps({
    items: Array,
    removeElement: Number
})

const totalSumCart = (itemPrice) => {
    emit('totalSum', itemPrice)
}

const newItemInCart = (item) => {
    emit('newItem', item)
}

const checkedState = (state) => {
    emit('isChecked', state)
}

</script>

<style scoped>
.cards {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    justify-items: center;
    gap: 20px;
}

@media (max-width:1198px) {
    .cards {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
    }
}

@media (max-width:910px) {
    .cards {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
    }
}

</style>