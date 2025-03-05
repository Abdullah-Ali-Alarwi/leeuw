<template>
  <div>
    <Nav />
    <router-view></router-view>
    <FooterVue />
    
    <button v-show="showButton" @click="scrollToTop" class="back-to-top">
      &#8679;
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import Nav from './component/Nav.vue';
import FooterVue from './component/Footer.vue';

const showButton = ref(false);

const handleScroll = () => {
  showButton.value = window.scrollY > 200;
};

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' });
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style>
.back-to-top {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background-color: rgba(244, 223, 127, 0.335);
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 24px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}
.back-to-top:hover {
  background-color: rgb(232, 180, 13);
}
</style>