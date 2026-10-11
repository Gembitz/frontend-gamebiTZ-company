<script setup>
import logoGame from '../assets/LogoGame.png'

const emit = defineEmits(['navigate'])

const currentYear = new Date().getFullYear()

const quickLinks = [
  { label: 'Home', target: 'Home' },
  { label: 'Product', target: 'Product' },
  { label: 'About me', target: 'About me' },
  { label: 'Contact', target: 'Contact' }
]

const legalLinks = [
  { label: 'Privacy Policy', href: '#' },
  { label: 'Terms of Service', href: '#' },
  { label: 'Cookie Settings', href: '#' }
]
</script>

<template>
  <footer class="app-footer">
    <div class="footer-container">
      <!-- Bagian Atas Footer: Brand & Navigasi Cepat Sederhana -->
      <div class="footer-top-row">
        <!-- Brand Logo & Nama GameDev -->
        <div class="footer-brand">
          <div class="brand-logo-wrapper">
            <img :src="logoGame" alt="GamebiTZ Logo" class="brand-logo-img" />
            <span class="brand-title">GamebiTZ</span>
          </div>
          <p class="brand-tagline">
            Studio game inovatif yang menghadirkan pengalaman bermain dan aset kreatif berkualitas tinggi.
          </p>
        </div>

        <!-- Menu Navigasi Sederhana -->
        <nav class="footer-nav">
          <ul class="nav-links-list">
            <li v-for="link in quickLinks" :key="link.label">
              <a 
                href="#" 
                class="nav-link-item"
                @click.prevent="emit('navigate', link.target)"
              >
                {{ link.label }}
              </a>
            </li>
          </ul>
        </nav>
      </div>

      <!-- Garis Pemisah Minimalis -->
      <div class="footer-divider"></div>

      <!-- Bagian Bawah: Copyright & Legal Links -->
      <div class="footer-bottom-row">
        <p class="copyright-text">
          &copy; {{ currentYear }} <strong>GamebiTZ</strong>. Seluruh hak cipta dilindungi.
        </p>

        <div class="legal-links-list">
          <a 
            v-for="legal in legalLinks" 
            :key="legal.label" 
            :href="legal.href" 
            class="legal-link-item"
          >
            {{ legal.label }}
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.app-footer {
  width: 100%;
  background-color: #ffffff;
  border-top: 1px solid #e2e8f0;
  padding: 3rem 0 2rem;
  box-sizing: border-box;
}

.footer-container {
  max-width: 1140px;
  margin: 0 auto;
  padding: 0 1.5rem;
  box-sizing: border-box;
}

/* Row Atas: Brand kiri & Menu kanan */
.footer-top-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
  flex-wrap: wrap;
}

.footer-brand {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  max-width: 380px;
}

.brand-logo-wrapper {
  display: flex;
  align-items: center;
  gap: 0.65rem;
}

.brand-logo-img {
  height: 32px;
  width: auto;
  object-fit: contain;
}

.brand-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: #000000;
  letter-spacing: -0.4px;
}

.brand-tagline {
  font-size: 0.85rem;
  line-height: 1.5;
  color: #64748b;
  margin: 0;
}

/* Navigasi horizontal di footer */
.footer-nav {
  display: flex;
  align-items: center;
}

.nav-links-list {
  display: flex;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 1.75rem;
  flex-wrap: wrap;
}

.nav-link-item {
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
  color: #334155;
  transition: color 0.2s ease;
}

.nav-link-item:hover {
  color: #00BCD4;
}

/* Garis Pemisah Minimalis */
.footer-divider {
  width: 100%;
  height: 1px;
  background-color: #f1f5f9;
  margin: 2rem 0 1.5rem;
}

/* Row Bawah: Hak Cipta & Kebijakan */
.footer-bottom-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1rem;
  flex-wrap: wrap;
}

.copyright-text {
  font-size: 0.825rem;
  color: #94a3b8;
  margin: 0;
}

.copyright-text strong {
  color: #475569;
}

.legal-links-list {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

.legal-link-item {
  font-size: 0.825rem;
  color: #94a3b8;
  text-decoration: none;
  transition: color 0.2s ease;
}

.legal-link-item:hover {
  color: #00BCD4;
}

/* Responsive Breakpoints */
@media (max-width: 768px) {
  .app-footer {
    padding: 2.5rem 0 1.5rem;
  }

  .footer-top-row {
    flex-direction: column;
    align-items: flex-start;
    gap: 1.5rem;
  }

  .nav-links-list {
    gap: 1.25rem;
  }

  .footer-bottom-row {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.75rem;
  }
}
</style>
