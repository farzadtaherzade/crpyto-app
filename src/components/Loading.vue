<template>
    <div class="loading"><span></span></div>
</template>
<script setup>
</script>
<style lang="scss" scoped>
.loading {
    height: 90vh;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    @keyframes circel-loading {
        to {
            transform: rotateZ(360deg);
        }
    }
    span {
        display: block;
        width: 70px;
        height: 70px;
        border-radius: 50%;
        border: 2px solid transparent;
        border-top-color: #000;
        animation: circel-loading 1200ms ease infinite;
    }
}
</style>