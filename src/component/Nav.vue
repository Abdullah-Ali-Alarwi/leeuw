<template>
  <nav class="container" style="width: 90%; margin: auto;">
    <main>
      <div class="logo">
        <img src="/src/assets/logo.png" alt="Logo">
      </div>

      <label for="menu-toggle" class="menu-icon" @click="menuOpen = !menuOpen">☰</label>

      <ul class="menu" :class="{ 'menu-open': menuOpen }">
        <li @click="closeMenu"><router-link :to="{ name: 'home' }">Home</router-link></li>
        <li @click="closeMenu"><router-link :to="{ name: 'about' }">About us</router-link></li>
        <li @click="closeMenu"><router-link :to="{ name: 'ourservices' }">Our Services</router-link></li>
        <li @click="closeMenu"><router-link :to="{ name: 'healthcareservies' }">Health Care Services</router-link></li>
        <li @click="closeMenu"><router-link :to="{ name: 'contactus' }">Contact Us</router-link></li>
      </ul>
    </main>
  </nav>
</template>

<script setup>
import { ref } from 'vue';

const menuOpen = ref(false);

const closeMenu = () => {
  menuOpen.value = false;
};
</script>

<style scoped>
main {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  position: relative;
}

.logo {
  width: 25%;
}

.logo img {
  width: 100%;
}

.menu {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  align-items: center;
}

.menu li {
  margin: 0 10px;
}

.menu a {
  font-size: 1.2vw;
  text-decoration: none;
  color: #D4AF37;
  padding: 2px 10px;
  display: block;
  width: fit-content;
}

.menu a:hover {
  background-color: rgba(194, 135, 135, 0.2);
  border-radius: 10px;
}

.menu-icon {
  display: none;
  font-size: 28px;
  cursor: pointer;
  color: #D4AF37;
}

@media (max-width: 820px) {
  .menu {
    display: flex;
    flex-direction: column;
    position: absolute;
    top: 60px;
    left: 0;
    width: 100%;
    background-color: rgba(33, 2, 28, 0.89);
    text-align: center;
    padding: 10px 0;
    transform: translateY(-20px);
    opacity: 0;
    pointer-events: none;
    transition: transform 0.3s ease-in-out, opacity 0.3s ease-in-out;
    z-index: 100;
  }


  .menu.menu-open {
    transform: translateY(0);
    opacity: 1;
    pointer-events: auto;
  }

  .menu li {
    padding: 10px 0;
  
  }

  

  .menu-icon {
    display: block;
  }

  .logo {
    width: 39%;
  }

  main {
    width: 100%;
  }
  a{
    font-size: 15px !important;
  }
}
</style>
