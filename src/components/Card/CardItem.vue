<template>
    <div class="card">
        <img class="sneakers-photo" :src="imageURL" alt="Sneakers">
        <h2 class="title-card">{{ title }}</h2>
        <div class="block-price">
            <div>
                <p class="price-text">ЦЕНА:</p>
                <p class="price">{{ price.toLocaleString('ru-RU') }} руб.</p>
            </div>
            <div>
                <img @click="toggleItemInCart" class="icon-plus" :src="currentImage" alt="Plus">
            </div>
        </div>
    </div>
</template>
<script setup>
import { onMounted, ref, watch, } from 'vue';
const emit = defineEmits(['itemPrice', 'newItem', 'isChecked']);

const props = defineProps({
    itemId: Number,
    imageURL: String,
    title: String,
    price: Number,
    removeElement: Number
})
const img1 = '/icons/plus.svg'
const img2 = '/icons/checked.svg'
const currentImage = ref(img1)

const handleItemRemoved = () => {
    if (props.removeElement === props.itemId) {
        currentImage.value = img1;
    }
};
watch(() => props.removeElement, () => {
    handleItemRemoved();
});

const toggleItemInCart = () => {
    currentImage.value = currentImage.value === img1 ? img2 : img1;
    const isChecked = currentImage.value === img2;
    saveCardState(props.itemId, isChecked);
    emit('itemPrice', currentImage.value === img2 ? props.price : -props.price)
    emit('isChecked', isChecked)

    const newItemInCart = {
        id: props.itemId,
        title: props.title,
        price: props.price,
        imageURL: props.imageURL,
    }

    emit('newItem', newItemInCart)
}

const saveCardState = (id, isChecked) => {
    const savedState = JSON.parse(localStorage.getItem('cardState')) || {};
    savedState[id] = isChecked;
    localStorage.setItem('cardState', JSON.stringify(savedState));
};

onMounted(() => {
    const savedState = JSON.parse(localStorage.getItem('cardState')) || {};
    if (savedState[props.itemId]) {
        currentImage.value = img2;
    }
});

window.addEventListener('reset-all-cards', () => {
    currentImage.value = img1;
});

</script>

<style scoped>
.card {
    position: relative;
    width: 210px;
    height: 289px;
    border: 2px solid #EAEAEA;
    border-radius: 40px;
    padding: 25px;
    transition: .2s;
    text-align: center;
    background-color: white;
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
</style>