<script setup>
import { ref } from "vue";

const image = ref([])

const props = defineProps(['icon'])
image.value.push(props.icon)
console.log(image.value[0])
</script>

<template>
  <div class="slider">
    <div class="slider-track">
      <div class="slide" v-for="icon in image[0][0]" :key="icon.id">
        <img :src="icon.image" :alt="icon.id" />
      </div>
      <div class="slide" v-for="icon in image[0][0]" :key="icon.id">
        <img :src="icon.image" :alt="icon.id" />
      </div>
    </div>
  </div>
</template>


<style lang="scss" scoped>
.slider {
  height: 140px;
  width: 100%;
  position: relative;
  display: grid;
  place-items: center;
  overflow: hidden;
  .slider-track {
    display: flex;
    width: 100%;
    align-items: center;
    animation: scroll 20s linear infinite;
    @keyframes scroll {
        0% {
            transform: translateX(0);
        }
        100% {
            transform: translateX(-50%);
        }

    }

    .slide {
      padding:20px;
      img {
        width: 50px;
        height: 50px;
      }
    }
  }
}
</style>