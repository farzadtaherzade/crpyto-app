<script setup>
import { onMounted, ref } from "vue";

const mobile = ref(false);
const mobileNav = ref(false);
const windowWidth = ref(null);

window.addEventListener("resize", checkScreen);
checkScreen();
function checkScreen() {
  windowWidth.value = window.innerWidth;
  if (windowWidth.value <= 750) {
    mobile.value = true;
    return;
  }
  mobile.value = false;
  return;
}

function toggleMobileNav() {
  mobileNav.value = !mobileNav.value;
}
</script>

<template>
  <header>
    <div
      class="menu-btn"
      v-show="mobile"
      @click="toggleMobileNav"
      :class="{ open: mobileNav }"
    >
      <div class="menu-btn-burger"></div>
    </div>

    <div class="left">
      <router-link to="#"><h1>Crypto</h1></router-link>
      <ul v-show="!mobile">
        <router-link to="#" class="link">
          <span>Home</span>
          <span class="slider"></span>
        </router-link>
        <a href="#" class="link">
          <span>Coin</span>
          <span class="slider"></span>
        </a>
        <a href="#" class="link">
          <span>Product</span>
          <span class="slider"></span>
        </a>
        <a href="#" class="link">
          <span>Message</span>
          <span class="slider"></span>
        </a>
      </ul>
    </div>

    <transition name="mobile-nav">
      <ul v-show="mobileNav" class="mobile-nav">
        <router-link to="#" class="link"> Home </router-link>
        <a href="#" class="link"> Coin </a>
        <a href="#" class="link"> Product </a>
        <a href="#" class="link"> Message </a>
      </ul>
    </transition>

    <div class="right">
      <!-- <form>
        <input type="text" class="search" placeholder="Search Coin" />
      </form> -->

      <div class="circel"></div>
    </div>
  </header>
</template>

<style scoped lang="scss">
header {
  width: 100%;
  height: 5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 10px;

  .menu-icon {
    display: flex;
    flex-direction: column;
    width: 50px;
    cursor: pointer;
    span {
      background: #000;
      border-radius: 10px;
      height: 7px;
      margin: 3px 0;
      transition: 0.4s cubic-bezier(0.68, -0.6, 0.32, 1.6);
      &:nth-of-type(1) {
        width: 60%;
      }
      &:nth-of-type(2) {
        width: 100%;
      }
      &:nth-of-type(3) {
        width: 75%;
      }
    }
  }

  .left {
    display: flex;
    align-items: center;
    justify-content: center;
    h1 {
      margin-right: 30px;
    }
    ul {
      display: flex;
      align-items: center;
      justify-content: center;
      .link {
        padding: 20px;
        font-size: 16px;
        transition: 0.3s;
        cursor: pointer;
        position: relative;
        display: inline-block;
        transition: all 0.3s ease-out;
        margin-right: 7px;
        &.router-link-active {
          .slider {
            width: 100%;
          }
          span {
            color: #e26d85;
          }
        }
        .slider {
          position: absolute;
          display: block;
          left: 0;
          top: 90%;
          margin: 0 auto;
          height: 2px;
          background-color: #e26d85;
          width: 0%;
          transition: width 1s ease;
        }

        &:hover {
          .slider {
            width: 100%;
          }
        }
        &:hover {
          span {
            color: #e26d85;
          }
        }
      }
    }
  }
  .right {
    display: flex;
    align-items: center;
    form {
      .search {
        border-radius: 20px;
        width: 12rem;
        padding: 8px 20px;
        outline: none;
        // margin-right: 20px;
      }
    }

    .circel {
      width: 30px;
      height: 30px;
      background-color: #e26d85;
      border-radius: 50%;
    }
  }

  .mobile-nav {
    width: 100%;
    height: 100%;
    max-width: 250px;
    display: flex;
    align-items: center;
    flex-direction: column;
    position: fixed;
    top: 0;
    right: 0;
    background-color: #fff;
    transition: all 0.7s ease;
    z-index: 999;
    .link {
      width: 100%;
      padding: 13px;
      margin: 3px;
      transition: 0.1s;
      border-top-left-radius: 4px;
      border-bottom-left-radius: 4px;
      &:hover {
        background-color: rgb(231, 76, 60, 0.03);
      }
    }
    .router-link-active {
      background-color: rgb(231, 76, 60, 0.03);
      border-left: 5px solid rgb(231, 76, 60);
    }
  }
  .mobile-nav-leave-active,
  .mobile-nav-enter-active {
    transition: all 0.7s ease;
  }
  .mobile-nav-enter-from,
  .mobile-nav-leave-to {
    transform: translateX(250px);
  }
  .mobile-nav-enter-to {
    transform: translateX(0px);
  }

  .menu-btn {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    // width: 30px;
    // height: 30px;
    cursor: pointer;
    // border: 1px solid #fff;
    transition: all 0.5s ease-in-out;
    .menu-btn-burger {
      width: 25px;
      height: 2px;
      background-color: #000;
      // border-radius: ;
      box-shadow: 0 2px 5px rgba(255, 101, 75, 0.2);
      transition: all 0.5s ease-in-out;
      &::after,
      &::before {
        content: "";
        position: absolute;
        width: 25px;
        height: 2px;
        background-color: #000;
        box-shadow: 0 2px 5px rgba(255, 101, 75, 0.2);
        transition: all 0.5s ease-in-out;
      }
      &::before {
        transform: translateY(-7px);
      }
      &::after {
        transform: translateY(7px);
      }
    }
  }
  .open .menu-btn-burger {
    transform: translateX(-50px);
    background: transparent;
    box-shadow: none;
    &::before {
      transform: rotate(45deg) translate(35px, -35px);
    }
    &::after {
      transform: rotate(-45deg) translate(35px, 35px);
    }
  }

  @media (max-width: 900px) {
    .search {
      display: none;
    }
  }
  @media (max-width: 768px) {
    .left {
      justify-content: center;
    }
  }
}
</style>
