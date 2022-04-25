<script setup>
import { ref } from "@vue/reactivity";

const coins = ref([]);
const coinRight = ref([]);
const props = defineProps(["coin", "coinRight"]);
coins.value.push(props.coin);
coinRight.value.push(props.coinRight);
console.log(coins.value);
</script>

<template>
  <div class="coins">
    <div class="coin-container__left">
      <div class="left__coin" v-for="coin in coins[0][0]" :key="coin">
        <img :src="coin.image" :alt="coin.name" />
        <span>{{ coin.name }}</span>
        <div class="num">
          <h1>{{ coin.current_price.toLocaleString() }}</h1>
          <span>{{ coin.symbol.toUpperCase() }}</span>
        </div>
      </div>
    </div>
    <div class="coin-container__right">
      <div class="right__coin" v-for="coin in coinRight[0][0]" :key="coin">
        <div class="image">
          <img :src="coin.image" :alt="coin.name" />
        </div>

        <div class="name">
          <h3>{{ coin.name }}</h3>
          <small>{{ coin.symbol.toUpperCase() }}</small>
        </div>

        <div class="price">
          <h3>Market Cap</h3>
          <small>${{ coin.market_cap.toLocaleString() }}</small>
        </div>
        <div class="price two">
          <h3>Market Cap</h3>
          <small>${{ coin.market_cap.toLocaleString() }}</small>
        </div>
        <div class="price three">
          <h3>Market Cap</h3>
          <small>${{ coin.market_cap.toLocaleString() }}</small>
        </div>

        <div class="change">
          <h3>Market Cap</h3>
          <small
            :class="{
              red: coin.price_change_percentage_24h,
              green: coin.price_change_percentage_24h > 0,
            }"
            >{{ coin.price_change_percentage_24h.toFixed(1) }}%</small
          >
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.coins {
  margin-top: 20px;
  display: flex;
  align-items: flex-start;
  .coin-container__left {
    width: 300px;
    .left__coin {
      display: flex;
      flex-direction: column;
      margin-bottom: 50px;
      background-color: #4158d0;
      background-image: linear-gradient(
        43deg,
        #4158d0 0%,
        #c850c0 46%,
        #ffcc70 100%
      );
      &:nth-of-type(2n) {
        background: #373b44; /* fallback for old browsers */
        background: -webkit-linear-gradient(
          to right,
          #4286f4,
          #373b44
        ); /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(
          to right,
          #4286f4,
          #373b44
        ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
      }
      &:nth-of-type(3n) {
        background: #8e2de2; /* fallback for old browsers */
        background: -webkit-linear-gradient(
          to right,
          #4a00e0,
          #8e2de2
        ); /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(
          to right,
          #4a00e0,
          #8e2de2
        ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
      }
      &:nth-of-type(4n) {
        background-color: #ffe53b;
        background-image: linear-gradient(147deg, #ffe53b 0%, #ff2525 74%);
      }

      padding: 30px;
      border-radius: 20px;
      box-shadow: 2.8px 2.8px 2.2px rgba(0, 0, 0, 0.008),
        6.7px 6.7px 5.3px rgba(0, 0, 0, 0.012),
        12.5px 12.5px 10px rgba(0, 0, 0, 0.015),
        22.3px 22.3px 17.9px rgba(0, 0, 0, 0.018),
        41.8px 41.8px 33.4px rgba(0, 0, 0, 0.022),
        100px 100px 80px rgba(0, 0, 0, 0.03);

      img {
        width: 2.53rem;
      }
      span {
        color: #ccc;
      }
      .num {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        width: 100%;
        color: #fff;
      }
    }
  }
  .coin-container__right {
    width: 100%;
    margin-left: 50px;

    .right__coin {
      margin-bottom: 20px;
      width: 100%;
      padding: 25px;
      border-radius: 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      box-shadow: 1.5px 2.1px 27.6px rgba(0, 0, 0, 0.01),
        3.2px 4.5px 57.6px rgba(0, 0, 0, 0.021),
        5.7px 8.2px 91.1px rgba(0, 0, 0, 0.032),
        10.3px 14.7px 130.9px rgba(0, 0, 0, 0.044),
        19.8px 28.2px 183.8px rgba(0, 0, 0, 0.056),
        52px 74px 325px rgba(0, 0, 0, 0.07);

      .image {
        width: 5.2vw;
        // padding: 0 0 0 10px;
        // border-left: 1px solid #ccc;
        img {
          width: 3rem;
        }
      }
      .name {
        width: 4rem;
        // padding: 0 0 0 10px;
        // border-left: 1px solid #ccc;
        display: flex;
        flex-direction: column;
        small {
          background-color: #8bc6ec;
          background-image: linear-gradient(135deg, #8bc6ec 0%, #9599e2 100%);

          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
        }
      }
      .price {
        width: 7rem;
        // padding: 0 0 0 10px;
        // border-left: 1px solid #ccc;
        display: flex;
        flex-direction: column;

        small {
          background-color: #8bc6ec;
          background-image: linear-gradient(135deg, #8bc6ec 0%, #9599e2 100%);

          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
        }
      }
      .change {
        // border-left: 1px solid #ccc;
        // padding: 0 0 0 10px;
        display: flex;
        flex-direction: column;
      }

      @media (max-width: 600px) {
        .image {
          img {
            width: 1.5rem;
          }
        }
        .name {
          h3 {
            font-size: 0.6rem;
          }
        }
        .price {
          h3 {
            font-size: 0.6rem;
          }
          &.two,
          &.three {
            display: none;
          }
        }
        .change {
          h3 {
            font-size: 0.6rem;
          }
        }
      }
      @media (max-width: 1024px) {
        .image {
          h3 {
            font-size: 16px;
          }
        }
        .name {
          h3 {
            font-size: 16px;
          }
        }
        .price {
          h3 {
            font-size: 16px;
          }
          &.two,
          &.three {
            display: none;
          }
        }
        .change {
          h3 {
            font-size: 16px;
          }
        }
      }
    }
  }
  @media (max-width: 768px) {
    flex-direction: column;
    align-items: center;
    .coin-container__left {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      .left__coin {
        width: 250px;
      }
    }
    .coin-container__right {
      margin-left: 0;
    }
  }
  @media (max-width: 521px) {
    .coin-container__left {
      justify-content: center;
    }
  }
}
</style>
