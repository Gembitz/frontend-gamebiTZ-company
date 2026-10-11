<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import ProductSection from './components/ProductSection.vue'
import PartnerSection from './components/PartnerSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'

const currentMenu = ref('Home')

// Mapping nama menu ke ID section target
const sectionMap = {
  'Home': 'home',
  'Product': 'product',
  'About me': 'about',
  'Contact': 'contact'
}

const handleNavigate = (menuName) => {
  currentMenu.value = menuName
  const targetId = sectionMap[menuName]
  if (targetId) {
    const targetElement = document.getElementById(targetId)
    if (targetElement) {
      // Offset 72px agar tidak tertutup header sticky
      const headerOffset = 72
      const elementPosition = targetElement.getBoundingClientRect().top
      const offsetPosition = elementPosition + window.pageYOffset - headerOffset

      window.scrollTo({
        top: offsetPosition,
        behavior: 'smooth'
      })
    }
  }
}

const handleLogin = () => {
  alert('Fitur login GamebiTZ akan segera hadir!')
}

const handleContact = () => {
  handleNavigate('Contact')
}

const handleJoin = () => {
  alert('Terima kasih telah bergabung bersama GamebiTZ!')
}

// Scrollspy sederhana: update menu aktif otomatis saat user scroll manual
let observer = null

onMounted(() => {
  const sections = ['home', 'product', 'about', 'contact']
  const reverseMap = {
    'home': 'Home',
    'product': 'Product',
    'about': 'About me',
    'contact': 'Contact'
  }

  observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        currentMenu.value = reverseMap[entry.target.id] || 'Home'
      }
    })
  }, {
    rootMargin: '-30% 0px -60% 0px'
  })

  sections.forEach((id) => {
    const el = document.getElementById(id)
    if (el) observer.observe(el)
  })
})

onUnmounted(() => {
  if (observer) observer.disconnect()
})
</script>

<template>
  <div class="app-root">
    <!-- Header Component -->
    <AppHeader 
      :active-menu="currentMenu"
      @navigate="handleNavigate"
      @login="handleLogin"
    />

    <!-- Main Content -->
    <main>
      <!-- Hero Section Component -->
      <HeroSection 
        @contact="handleContact"
        @join="handleJoin"
      />

      <!-- Product Section Component -->
      <ProductSection />

      <!-- Partner Section (Ticker Baris Mitra di bawah Produk) -->
      <PartnerSection />

      <!-- About Us Component (Tentang Kami) -->
      <AboutSection />

      <!-- Contact Section Component -->
      <ContactSection />
    </main>

    <!-- Footer Component Sederhana -->
    <AppFooter @navigate="handleNavigate" />
  </div>
</template>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  width: 100%;
  overflow-x: hidden;
  font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  background-color: #ffffff;
}

.app-root {
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  width: 100%;
  flex: 1;
}
</style>
