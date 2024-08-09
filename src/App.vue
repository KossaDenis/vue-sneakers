<template>
    <Drawer v-if="stateDrawer" @closeDrawer="closeDrawer" @emptyArray="assignEmptyArray" :itemsCart="newItemCart"
        :totalSumCart="totalSumCart" @removeItemCart="removeItemCart" />
    <div class="main-block">
        <Header :totalSumCart="totalSumCart" @openDrawer="openDrawer" :newItemCart="newItemCart" />
        <Content :loading="loading" :items="items" :removeElement="removeElement" @search="searchElements"
            @sort="sortedElements" @totalSum="totalSum" @newItem="sentItemCart" @isChecked="checkedState" />

    </div>
</template>

<script setup>
import { onMounted, ref, watch } from 'vue';

import Header from './components/Header.vue'
import Content from './components/Content.vue';
import Drawer from './components/Cart/Drawer.vue';
import axios from 'axios';

const originalItems = ref([]);
const items = ref([]);
const searchText = ref('');
const sortMethod = ref('default');
const loading = ref(true);
const totalSumCart = ref(0);
const stateDrawer = ref();
const newItemCart = ref([]);
const checkState = ref(false);
const removeElement = ref();


onMounted(async () => {
    loading.value = true
    try {
        const { data } = await axios.get('https://604781a0efa572c1.mokky.dev/items?limit=12');
        const elements = data.items;
        originalItems.value = elements;
        items.value = elements;
    } catch {
        console.log('Данные не смогли прийти');
    } finally {
        loading.value = false
    }
    const stateSum = localStorage.getItem('totalSumCart')
    totalSumCart.value = parseFloat(stateSum)

    const stateItemsCart = localStorage.getItem('itemsCart')
    newItemCart.value = JSON.parse(stateItemsCart)
})

watch(stateDrawer, (newValue) => {
    if (newValue) {
        document.body.classList.add('no-scroll');
    } else {
        document.body.classList.remove('no-scroll');
    }
})

const FiltersAndSorting = () => {
    let filteredItems = originalItems.value.filter(item =>
        item.title.toLowerCase().includes(searchText.value.toLowerCase().trim())
    );

    switch (sortMethod.value) {
        case 'default':
            filteredItems.sort((a, b) => a.id - b.id);
            break;
        case 'name':
            filteredItems.sort((a, b) => a.title.localeCompare(b.title));
            break;
        case 'priceAscending':
            filteredItems.sort((a, b) => a.price - b.price);
            break;
        case 'priceDescending':
            filteredItems.sort((a, b) => b.price - a.price);
            break;
        default:
            break;
    }

    items.value = filteredItems;
};

const searchElements = (text) => {
    searchText.value = text;
    FiltersAndSorting();
};

const sortedElements = (method) => {
    sortMethod.value = method;
    FiltersAndSorting();
};

const totalSum = (itemPrice) => {
    totalSumCart.value += itemPrice
    localStorage.setItem('totalSumCart', totalSumCart.value);
}

const openDrawer = (state) => {
    stateDrawer.value = state
}

const closeDrawer = () => {
    stateDrawer.value = false
}

const sentItemCart = (item) => {
    if (checkState.value) {
        newItemCart.value.push(item)
    } else {
        newItemCart.value = newItemCart.value.filter(itemCart => itemCart.id !== item.id)
    }
    localStorage.setItem('itemsCart', JSON.stringify(newItemCart.value))
}

const checkedState = (state) => {
    checkState.value = state
}

const assignEmptyArray = (emptyArray) => {
    newItemCart.value = emptyArray
    localStorage.setItem('itemsCart', JSON.stringify(newItemCart.value));

    totalSumCart.value = newItemCart.value.reduce((acc, item) => acc + item.price, 0);
    localStorage.setItem('totalSumCart', totalSumCart.value);

    const savedState = JSON.parse(localStorage.getItem('cardState')) || {};
    for (const itemId in savedState) {
        savedState[itemId] = false; 
    }
    localStorage.setItem('cardState', JSON.stringify(savedState));

    resetAllCards()
}

const resetAllCards = () => {
    const resetEvent = new Event('reset-all-cards');
    window.dispatchEvent(resetEvent);
};

const removeItemCart = (itemId) => {
    newItemCart.value = newItemCart.value.filter(itemCart => itemCart.id !== itemId)
    localStorage.setItem('cardState', JSON.stringify(newItemCart.value));
    localStorage.setItem('itemsCart', JSON.stringify(newItemCart.value));

    totalSumCart.value = newItemCart.value.reduce((acc, item) => acc + item.price, 0);
    localStorage.setItem('totalSumCart', totalSumCart.value);
    removeElement.value = itemId
}

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