<script setup>
import { ref, watch, onMounted, onUnmounted } from 'vue'
import logoGame from '../assets/LogoGame.png'

const props = defineProps({
  activeMenu: {
    type: String,
    default: 'Home'
  }
})

const emit = defineEmits(['navigate', 'login'])

const menus = [
  { name: 'Home', label: 'Home' },
  { name: 'Product', label: 'Product' },
  { name: 'About me', label: 'About me' },
  { name: 'Contact', label: 'Contact' }
]

const currentActive = ref(props.activeMenu)
watch(() => props.activeMenu, (newVal) => {
  currentActive.value = newVal
})
const isScrolled = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 10
}

const selectMenu = (name) => {
  currentActive.value = name
  emit('navigate', name)
}

const handleLogin = () => {
  emit('login')
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header class="app-header" :class="{ 'scrolled': isScrolled }">
    <div class="header-container">
      <!-- Left: Logo & Brand Name -->
      <a href="#" class="brand" @click.prevent="selectMenu('Home')">
        <div class="brand-logo">
          <img :src="logoGame" alt="GameDev Logo" class="logo-image" />
        </div>
        <span class="brand-name">GamebiTZ</span>
      </a>

      <!-- Middle: Navigation Menus -->
      <nav class="nav-menu">
        <ul class="nav-list">
          <li v-for="menu in menus" :key="menu.name" class="nav-item">
            <a
              href="#"
              class="nav-link"
              :class="{ 'active': currentActive === menu.name }"
              @click.prevent="selectMenu(menu.name)"
            >
              {{ menu.label }}
            </a>
          </li>
        </ul>
      </nav>

      <!-- Right: Action Button -->
      <div class="header-action">
        <button class="btn-login" type="button" @click="handleLogin">
          Login
        </button>
      </div>
    </div>
  </header>
</template>

<style scoped>
.app-header {
  position: sticky;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  background-color: transparent;
  backdrop-filter: blur(0px);
  -webkit-backdrop-filter: blur(0px);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-sizing: border-box;
}

/* Glassmorphism & border effect on scroll */
.app-header.scrolled {
  background-color: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  box-shadow: 0 4px 20px -2px rgba(0, 0, 0, 0.06);
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
}

.header-container {
  width: 100%;
  padding: 0 2rem;
  height: 72px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-sizing: border-box;
}

/* Brand styling */
.brand {
  display: flex;
  align-items: center;
  gap: 0.65rem;
  text-decoration: none;
  cursor: pointer;
  user-select: none;
  transition: transform 0.2s ease;
}

.brand:hover {
  transform: translateY(-1px);
}

.brand-logo {
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.3s ease;
}

.logo-image {
  height: 36px;
  width: auto;
  object-fit: contain;
  display: block;
}

.brand:hover .brand-logo {
  transform: scale(1.05);
}

.brand-name {
  font-size: 1.35rem;
  font-weight: 700;
  color: #000000;
  letter-spacing: -0.5px;
}

/* Navigation Menu */
.nav-menu {
  display: flex;
  align-items: center;
}

.nav-list {
  display: flex;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 2rem;
}

.nav-item {
  position: relative;
}

.nav-link {
  display: inline-block;
  padding: 0.5rem 0.1rem;
  text-decoration: none;
  font-size: 1rem;
  font-weight: 500;
  color: #000000;
  position: relative;
  transition: color 0.25s ease;
}

.nav-link:hover {
  color: #2196F3;
}

/* Active Menu Item & Underline indicator */
.nav-link.active {
  color: #2196F3;
  font-weight: 600;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0%;
  height: 2.5px;
  background-color: #2196F3;
  border-radius: 99px;
  transition: width 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.nav-link.active::after {
  width: 100%;
}

.nav-link:not(.active):hover::after {
  width: 50%;
  opacity: 0.5;
}

/* Right Login Button */
.header-action {
  display: flex;
  align-items: center;
}

.btn-login {
  background-color: #2196F3;
  color: #ffffff;
  border: none;
  outline: none;
  font-size: 0.95rem;
  font-weight: 600;
  padding: 0.6rem 1.6rem;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.25s ease;
  box-shadow: 0 4px 12px rgba(33, 150, 243, 0.28);
}

.btn-login:hover {
  background-color: #1976D2;
  box-shadow: 0 6px 18px rgba(33, 150, 243, 0.4);
  transform: translateY(-2px);
}

.btn-login:active {
  transform: translateY(0);
  box-shadow: 0 2px 8px rgba(33, 150, 243, 0.3);
}

/* Responsive adjustment */
@media (max-width: 768px) {
  .header-container {
    padding: 0 1rem;
    height: 64px;
  }

  .nav-list {
    gap: 1.1rem;
  }

  .brand-name {
    font-size: 1.15rem;
  }

  .nav-link {
    font-size: 0.9rem;
  }

  .btn-login {
    padding: 0.5rem 1.2rem;
    font-size: 0.88rem;
  }
}
</style>
