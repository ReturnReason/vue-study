<template>
  <div>
    <transition name="fade">
      <ModalPage :items="items" :index="index" @modalClose="isModalOpen = false" v-if="isModalOpen" />
    </transition>

    <nav class="nav-container">
      <div class="nav">
        <a class="logo" href="#">LOGO</a>
        <ul class="nav-menu">
          <li v-for="menuItem in menu" :key="menuItem">{{ menuItem }}</li>
        </ul>
      </div>
    </nav>

    <div class="header-bg">
      <div class="blur-bg"></div>
      <h1 class="header-text">REASON SHOP</h1>
    </div>

    <div>
      <p @click="click" class="text-add-item">신규 상품 추가</p>
    </div>

    <div class="item-container">
      <div
        @click="
          isModalOpen = true;
          index = i;
        "
        class="item-list"
        v-for="(item, i) in items"
        :key="i"
      >
        <ul class="item">
          <img :src="require(`./assets/${item.img}.jpg`)" alt="" />
          <li class="item-name">{{ item.title }}</li>
          <li class="item-price">{{ item.price }}원</li>
        </ul>
        <button class="btn">구매하기</button>
      </div>
    </div>

    <div style="height: 500px"></div>
  </div>
</template>

<script>
import item from './assets/product.js';
import ModalPage from './components/ModalPage.vue';

export default {
  name: 'App',
  components: {
    ModalPage,
  },
  data() {
    return {
      menu: ['Home', 'About', 'menu3', 'menu4'],
      items: item,
      isModalOpen: false,
      index: 0,
    };
  },
  methods: {
    click: function () {
      console.log('클릭');
    },
  },
  props: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body,
h1,
h2,
h3,
p div,
ul {
  margin: 0;
  padding: 0;
}

div {
  box-sizing: border-box;
}

li {
  list-style: none;
}

/* 모달 페이드 */
.fade-enter-from {
  /* 시작시 효과 */
  opacity: 0;
}

.fade-enter-active {
  /* 전체 단계에서 적용될 부분*/
  transition: all 1s;
}

.fade-enter-to {
  /* 끝나는 효과 */
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 1s;
}

.fade-leave-to {
  opacity: 0;
}

.nav-container {
  background: #2c3e50;
  color: white;
  margin: 0 auto;
}

.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  height: 50px;
  max-width: 1200px;
  margin: 0 auto;
}

.logo {
  text-decoration: none;
  font-size: 20px;
  color: white;
  margin-left: 20px;
}

.nav-menu {
  display: flex;
  align-items: center;
}

.nav-menu li {
  margin-left: 5px;
  margin-right: 5px;
}

.nav-menu li:last-child {
  margin-right: 20px;
}

/* 최상단 메인 이미지*/
.header-bg {
  background: linear-gradient(rgba(54, 82, 154, 0.5), rgba(10, 12, 15, 0.5)), url(./assets/bg.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  background-blend-mode: darken;
  width: 100%;
  margin: 0 auto;
  margin-bottom: 50px;
  height: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-position: center;
  position: relative;
}

.blur-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(5px);
  position: absolute;
}

.header-text {
  color: #fff;
  font-size: 50px;
  z-index: 2;
}
/* 상품 위 텍스트 */
.text-add-item {
  font-size: 20px;
  font-weight: 900;
  border: none;
  border-bottom: 2px solid #eee;
  max-width: 1200px;
  margin: 0 auto;
  padding-bottom: 50px;
  margin-bottom: 30px;
}

/* 상품들 */

.item-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  max-width: 1200px;
  gap: 30px;
  margin: 0 auto;
}

.item-list {
  padding: 10px;
  border: 1px solid #eee;
  border-radius: 5px;
  height: 100%;
  transition: all 0.5s;
  transition-delay: 0.1s;
}

.item-list:hover {
  transform: scale(1.03);
  box-shadow: 2px 2px 10px #eee;
}

.item {
  width: 100%;
  padding: 0;
}

.item img {
  width: 100%;
  display: block;
  border-radius: 5px;
  height: 400px;
  margin: 0 auto;
  object-fit: cover;
  object-position: center;
}

.item-name {
  font-size: 1.2rem;
  font-weight: 900;
  margin-top: 10px;
  margin-bottom: 5px;
}

.item-price {
  font-size: 1rem;
  margin-bottom: 10px;
}

.btn {
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  color: #fff;
  background: #2c3e50;
  width: 100%;
}
</style>
