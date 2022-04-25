<script setup>
</script>

<template>
  <div class="main">
    <div class="left">
      <h1>The Best Trading Crpytocurrency Assets</h1>
      <p>Buy and Sell crpytocurrency with the best quality and easy</p>
      <a class="button">Buy Now</a>
    </div>
    <div class="right">
      <img src="../assets/02d7dad6-972c-4413-8883-c809324b2b7a.jpeg" alt="" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.main {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 50px;

  .left {
    flex-basis: 50%;
    width: 100%;
    h1 {
      max-width: 30rem;
      line-height: 40px;
      font-size: 40px;
    }
    p {
      color: rgba($color: #000000, $alpha: 0.3);
      margin-top: 18px;
      font-size: 16px;
    }
    .button {
      display: flex;
      align-items: center;
      justify-content: center;

      width: 125px;
      height: 50px;
      margin-top: 30px;
      background-color: #e26d85;
      color: #fff;
      border-radius: 88px;
    }
  }
  .right {
    flex-basis: 50%;
    width: 100%;
    img {
      width: 100%;
      border-radius: 20px;
    }
  }
}
@media (max-width: 900px) {
  .main {
    .right {
      flex-basis: none;
      display: none;
    }
    .left {
      flex-basis: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
      h1 {
        max-width: 1300px;
        font-size: 30px;
      }
    }
  }
}
</style>
