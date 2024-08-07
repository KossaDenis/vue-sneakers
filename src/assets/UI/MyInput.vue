<template>
    <input @input="$emit('update:modelValue', $event.target.value)" :value="modelValue" class="my-input" type="text">
</template>

<script setup>
defineProps({
    modelValue: String
}) 
</script>

<style scoped>
.my-input {
    width: 250px;
    padding: 13px 15px 13px 46px;
    border: 2px solid #EAEAEA;
    border-radius: 10px;
    outline: none;
}

.my-input:focus {
    border: 2px solid #b3b3b3;
}
</style>