<template>
  <div class="app-container"
       style='font-family: Inter, "Noto Sans", sans-serif;'>
    <Header/>
    <main class="main-content">
      <router-view></router-view>
    </main>
    <Footer/>
  </div>
</template>

<script setup lang="ts">
import './assets/styles/main.css'
import {ref, onMounted, onUnmounted} from 'vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

// Scroll to top functionality
const showScrollTop = ref(false)

const checkScroll = () => {
  showScrollTop.value = window.scrollY > 500
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

onMounted(() => {
  window.addEventListener('scroll', checkScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', checkScroll)
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;900&family=Noto+Sans:wght@400;500;700;900&display=swap');
</style>
