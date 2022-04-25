<script setup>
import Main from "../components/Main.vue";
import CoinSlider from "../components/CoinSlider.vue";
import Coins from "../components/Coins.vue";
import { onMounted, ref } from "vue";
import axios from "axios";

const coinLeft = ref([]);
const coinRight = ref([]);

const coinImages = ref([]);
const isLoaded = ref(true);
axios
  .get(
    "https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false"
  )
  .then((res) => {
    coinImages.value.push(res.data.slice(0, 30));
    coinLeft.value.push(res.data.slice(0, 4));
    coinRight.value.push(res.data.slice(0, 30));
  })
  .catch((err) => {
    console.log(err);
  });
// console.log(coin.value)
onMounted(() => {
  document.onreadystatechange = () => {
    if (document.readystate == "complete") {
      isLoaded.value = true;
    }
  };
});
</script>

<template>
  <div class="home">
    <Main />
    <CoinSlider :icon="coinImages" />
    <Coins :coin="coinLeft" :coinRight="coinRight" />
  </div>
</template>
