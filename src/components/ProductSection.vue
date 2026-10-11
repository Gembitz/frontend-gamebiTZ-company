<script setup>
import { ref, computed } from 'vue'
import prodGame from '../assets/prod_game.jpg'
import prodAssets from '../assets/prod_assets.jpg'

// Kategori sisi kiri
const categories = [
  { id: 'all', label: 'All' },
  { id: 'game', label: 'Game' },
  { id: 'assets', label: 'Assets Game' },
  { id: 'console', label: 'Console' },
  { id: 'merchandise', label: 'Merchandise' },
  { id: 'animation', label: 'Animasi' }
]

const activeCategory = ref('all')

// Data produk GameDev (hasil game, asset game, console, merchandise, animasi)
const allProducts = ref([
  {
    id: 1,
    title: 'Neon Overdrive: Cybernetic',
    category: 'Game',
    categoryId: 'game',
    image: prodGame
  },
  {
    id: 2,
    title: 'RPG Fantasy Ultimate Asset Pack',
    category: 'Assets Game',
    categoryId: 'assets',
    image: prodAssets
  },
  {
    id: 3,
    title: 'GDev Portable OLED Pro',
    category: 'Console',
    categoryId: 'console',
    svgType: 'console',
    gradient: 'linear-gradient(135deg, #1e1b4b 0%, #312e81 100%)'
  },
  {
    id: 4,
    title: 'Mecha Cyber Jacket & Cap',
    category: 'Merchandise',
    categoryId: 'merchandise',
    svgType: 'merch',
    gradient: 'linear-gradient(135deg, #064e3b 0%, #047857 100%)'
  },
  {
    id: 5,
    title: 'Chronicles: The Lost Odyssey',
    category: 'Animasi',
    categoryId: 'animation',
    svgType: 'animation',
    gradient: 'linear-gradient(135deg, #4c0519 0%, #881337 100%)'
  },
  {
    id: 6,
    title: 'Shadow Realms Online',
    category: 'Game',
    categoryId: 'game',
    svgType: 'game-extra',
    gradient: 'linear-gradient(135deg, #0f172a 0%, #1e293b 100%)'
  },
  {
    id: 7,
    title: 'Sci-Fi Modular Mech 3D Rig',
    category: 'Assets Game',
    categoryId: 'assets',
    svgType: 'assets-extra',
    gradient: 'linear-gradient(135deg, #164e63 0%, #0e7490 100%)'
  },
  {
    id: 8,
    title: 'Titan Controller Wireless V2',
    category: 'Console',
    categoryId: 'console',
    svgType: 'console-extra',
    gradient: 'linear-gradient(135deg, #3730a3 0%, #4338ca 100%)'
  }
])

// Filter produk berdasarkan kategori aktif
const filteredProducts = computed(() => {
  if (activeCategory.value === 'all') {
    return allProducts.value
  }
  return allProducts.value.filter(p => p.categoryId === activeCategory.value)
})

// Slider state & batasan: menampilkan 4 produk sekaligus
const VISIBLE_COUNT = 4
const currentIndex = ref(0)

const setCategory = (catId) => {
  activeCategory.value = catId
  currentIndex.value = 0 // Reset posisi slider ke awal saat kategori diubah
}

// Menentukan batas maksimal geser
const maxIndex = computed(() => {
  const total = filteredProducts.value.length
  return Math.max(0, total - VISIBLE_COUNT)
})

// Arrow kiri hanya muncul jika belum mentok kiri (currentIndex > 0)
const canScrollLeft = computed(() => {
  return currentIndex.value > 0
})

// Arrow kanan hanya muncul jika belum mentok kanan (currentIndex < maxIndex)
const canScrollRight = computed(() => {
  return currentIndex.value < maxIndex.value
})

const slideLeft = () => {
  if (canScrollLeft.value) {
    currentIndex.value--
  }
}

const slideRight = () => {
  if (canScrollRight.value) {
    currentIndex.value++
  }
}
</script>

<template>
  <section id="product" class="products-section">
    <div class="products-container">
      <!-- Section Header -->
      <div class="section-title-wrap">
        <span class="section-badge">Katalog GameDev</span>
        <h2 class="section-heading">Koleksi Produk & Kreasi Pilihan</h2>
      </div>

      <div class="products-layout">
        <!-- Sisi Kiri: Filter Kategori Vertikal -->
        <aside class="category-sidebar">
          <ul class="category-list">
            <li v-for="cat in categories" :key="cat.id" class="category-item">
              <button
                type="button"
                class="category-btn"
                :class="{ 'active': activeCategory === cat.id }"
                @click="setCategory(cat.id)"
              >
                {{ cat.label }}
              </button>
            </li>
          </ul>
        </aside>

        <!-- Sisi Kanan sampai Tengah: Slider Horizontal Produk & Tombol Panah -->
        <div class="slider-wrapper">
          <!-- Tombol Arrow Kiri (Otomatis hilang jika mentok kiri) -->
          <button
            v-if="canScrollLeft"
            type="button"
            class="slider-arrow arrow-left"
            aria-label="Geser ke kiri"
            @click="slideLeft"
          >
            <svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="15 18 9 12 15 6"></polyline>
            </svg>
          </button>

          <!-- Area Viewport Produk (Overflow Hidden) -->
          <div class="products-viewport">
            <div 
              class="products-track"
              :style="{ transform: `translateX(-${currentIndex * 25}%)` }"
            >
              <div 
                v-for="product in filteredProducts" 
                :key="product.id" 
                class="product-card"
              >
                <div class="product-image-box">
                  <!-- Gambar jika tersedia (jpg/png) -->
                  <img 
                    v-if="product.image" 
                    :src="product.image" 
                    :alt="product.title"
                    class="product-img" 
                  />
                  <!-- Visual SVG Dinamis untuk produk Console, Merchandise, & Animasi -->
                  <div 
                    v-else 
                    class="product-visual-placeholder"
                    :style="{ background: product.gradient }"
                  >
                    <!-- Console SVG -->
                    <svg v-if="product.svgType?.includes('console')" viewBox="0 0 24 24" width="56" height="56" fill="none" stroke="#ffffff" stroke-width="1.75">
                      <rect x="2" y="6" width="20" height="12" rx="4"></rect>
                      <line x1="6" y1="12" x2="10" y2="12"></line>
                      <line x1="8" y1="10" x2="8" y2="14"></line>
                      <circle cx="15.5" cy="10.5" r="1" fill="#00BCD4"></circle>
                      <circle cx="17.5" cy="13.5" r="1" fill="#00BCD4"></circle>
                    </svg>
                    <!-- Merchandise SVG -->
                    <svg v-else-if="product.svgType?.includes('merch')" viewBox="0 0 24 24" width="56" height="56" fill="none" stroke="#ffffff" stroke-width="1.75">
                      <path d="M20.38 3.46L16 2a4 4 0 01-8 0L3.62 3.46a2 2 0 00-1.34 2.23l.58 3.5a2 2 0 001.23 1.54L6 11.5V20a2 2 0 002 2h8a2 2 0 002-2v-8.5l1.91-.77a2 2 0 001.23-1.54l.58-3.5a2 2 0 00-1.34-2.23z"></path>
                    </svg>
                    <!-- Animation SVG -->
                    <svg v-else-if="product.svgType?.includes('animation')" viewBox="0 0 24 24" width="56" height="56" fill="none" stroke="#ffffff" stroke-width="1.75">
                      <rect x="2" y="2" width="20" height="20" rx="3"></rect>
                      <polygon points="10 8 16 12 10 16 10 8" fill="#00BCD4"></polygon>
                    </svg>
                    <!-- Default Game/Asset SVG -->
                    <svg v-else viewBox="0 0 24 24" width="56" height="56" fill="none" stroke="#ffffff" stroke-width="1.75">
                      <polygon points="12 2 2 7 12 12 22 7 12 2"></polygon>
                      <polyline points="2 17 12 22 22 17"></polyline>
                      <polyline points="2 12 12 17 22 12"></polyline>
                    </svg>
                  </div>
                </div>

                <!-- Detail Produk: Judul & Kategori -->
                <div class="product-info">
                  <h3 class="product-title" :title="product.title">{{ product.title }}</h3>
                  <span class="product-category">{{ product.category }}</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Tombol Arrow Kanan (Otomatis hilang jika mentok kanan) -->
          <button
            v-if="canScrollRight"
            type="button"
            class="slider-arrow arrow-right"
            aria-label="Geser ke kanan"
            @click="slideRight"
          >
            <svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
              <polyline points="9 18 15 12 9 6"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Background section sesuai permintaan: #F1F8FE */
.products-section {
  width: 100%;
  background-color: #F1F8FE;
  padding: 4rem 0 5rem;
  box-sizing: border-box;
}

.products-container {
  width: 100%;
  padding: 0 2rem;
  box-sizing: border-box;
}

.section-title-wrap {
  margin-bottom: 2.25rem;
}

.section-badge {
  display: inline-block;
  font-size: 0.85rem;
  font-weight: 600;
  color: #00BCD4;
  text-transform: uppercase;
  letter-spacing: 0.8px;
  margin-bottom: 0.5rem;
}

.section-heading {
  font-size: 2rem;
  font-weight: 800;
  color: #0f172a;
  margin: 0;
  letter-spacing: -0.5px;
}

/* Layout horizontal: Kiri Sidebar, Kanan Produk Slider */
.products-layout {
  display: flex;
  align-items: flex-start;
  gap: 2.5rem;
  width: 100%;
}

/* Sisi Kiri: List Vertikal Kategori */
.category-sidebar {
  width: 200px;
  flex-shrink: 0;
}

.category-list {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.category-btn {
  width: 100%;
  text-align: left;
  background: transparent;
  border: none;
  outline: none;
  padding: 0.75rem 1rem;
  font-size: 1rem;
  font-weight: 600;
  color: #475569;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.category-btn:hover {
  color: #00BCD4;
  background-color: rgba(0, 188, 212, 0.06);
}

/* Warna aktif kategori: #00BCD4 */
.category-btn.active {
  color: #00BCD4;
  background-color: rgba(0, 188, 212, 0.12);
  font-weight: 700;
}

/* Sisi Kanan/Tengah: Slider Wrapper */
.slider-wrapper {
  position: relative;
  flex: 1;
  min-width: 0;
  display: flex;
  align-items: center;
}

/* Tombol Arrow Navigasi diantara produk */
.slider-arrow {
  position: absolute;
  top: 40%;
  transform: translateY(-50%);
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background-color: #ffffff;
  color: #0f172a;
  border: 1px solid #e2e8f0;
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.12);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 10;
  transition: all 0.25s ease;
  outline: none;
}

.slider-arrow:hover {
  background-color: #00BCD4;
  color: #ffffff;
  border-color: #00BCD4;
  transform: translateY(-50%) scale(1.08);
  box-shadow: 0 8px 20px rgba(0, 188, 212, 0.35);
}

.arrow-left {
  left: -20px;
}

.arrow-right {
  right: -20px;
}

/* Viewport Slider Produk */
.products-viewport {
  width: 100%;
  overflow: hidden;
  border-radius: 12px;
}

.products-track {
  display: flex;
  transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
  will-change: transform;
}

/* Batasi menampilkan 4 produk sekaligus (width 25%) */
.product-card {
  flex: 0 0 25%;
  max-width: 25%;
  padding: 0 0.65rem;
  box-sizing: border-box;
}

.product-image-box {
  width: 100%;
  aspect-ratio: 1 / 1;
  border-radius: 16px;
  overflow: hidden;
  background-color: #ffffff;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
  display: flex;
  align-items: center;
  justify-content: center;
}

.product-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.product-visual-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Detail info produk: judul & kategori di bawahnya */
.product-info {
  margin-top: 0.85rem;
  padding: 0 0.2rem;
}

.product-title {
  font-size: 1rem;
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 0.3rem 0;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.product-category {
  font-size: 0.85rem;
  font-weight: 500;
  color: #64748b;
  display: block;
}

/* Responsive Breakpoints */
@media (max-width: 1200px) {
  /* Tampilkan 3 produk di layar tablet/sedang */
  .product-card {
    flex: 0 0 33.333%;
    max-width: 33.333%;
  }
}

@media (max-width: 900px) {
  .products-layout {
    flex-direction: column;
    gap: 1.5rem;
  }

  .category-sidebar {
    width: 100%;
  }

  .category-list {
    flex-direction: row;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .category-btn {
    width: auto;
    padding: 0.5rem 1rem;
  }

  .product-card {
    flex: 0 0 50%;
    max-width: 50%;
  }
}

@media (max-width: 580px) {
  .product-card {
    flex: 0 0 100%;
    max-width: 100%;
  }

  .arrow-left {
    left: -10px;
  }

  .arrow-right {
    right: -10px;
  }
}
</style>
