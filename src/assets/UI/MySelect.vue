<template>
    <select class="select">
        <slot></slot>
    </select>
</template>

<script>
export default {

}
</script>

<style scoped>
.select {
    padding: 10px 15px;
    border: 2px solid #EAEAEA;
    border-radius: 10px;
    outline: none;
}

.select:focus {
    border: 2px solid #b3b3b3;
}
</style>