<template>
  <div>
    <CartItem v-for="item in itemsCart" :key="item.id" :id="item.id" :imageURL="item.imageURL" :title="item.title"
      :price="item.price" @removeItemCart="removeItem" />
  </div>
</template>

<script setup>
import CartItem from '@/components/Cart/CartItem.vue'

const emit = defineEmits(['removeItemCart'])

const props = defineProps({
  itemsCart: Array,
})

const removeItem = (item) => {
  emit('removeItemCart', item)
}


</script>

<style scoped></style>