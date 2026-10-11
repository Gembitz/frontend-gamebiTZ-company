<script setup>
import heroIllustration from '../assets/hero_game_transparent.png'

const emit = defineEmits(['contact', 'join'])

const features = [
  {
    title: 'High Performance Engine',
    desc: 'Pengembangan game teroptimasi dengan frame-rate tinggi dan latensi ultra rendah.'
  },
  {
    title: 'Creative Art & Design',
    desc: 'Desain karakter orisinal, kendaraan futuristik, dan persenjataan visual sinematik.'
  },
  {
    title: 'Multiplatform Ready',
    desc: 'Ekosistem game lintas platform (PC, Mobile, & Konsol) didukung cloud multiplayer.'
  }
]
</script>

<template>
  <section id="home" class="hero-section">
    <!-- Shape Persegi Dekoratif di Sisi Kanan Atas (#BBDEFB) -->
    <div class="accent-shape-box" aria-hidden="true"></div>

    <div class="hero-container">
      <!-- Grid Utama: Content Kiri & Gambar Kanan -->
      <div class="hero-main-grid">
        <!-- Sisi Kiri: Sambutan, Deskripsi, Tombol Aksi, dan Kelebihan di bawah tombol -->
        <div class="hero-content">
          <span class="hero-badge">Selamat Datang di Dunia Inovasi Game</span>
          <h1 class="hero-title">
            Wujudkan Dunia Game Impian Bersama <span class="highlight-text">GamebiTZ</span>
          </h1>
          <p class="hero-description">
            Kami adalah studio pengembang game terdepan yang menghadirkan pengalaman visual imersif, mekanik gameplay mutakhir, serta karakter dan dunia interaktif luar biasa untuk para gamer di seluruh dunia.
          </p>

          <div class="hero-cta-group">
            <button class="btn-contact" type="button" @click="emit('contact')">
              Contact Me
            </button>
            <button class="btn-join" type="button" @click="emit('join')">
              Join Now
            </button>
          </div>

          <!-- 3 Kelebihan Perusahaan disusun horizontal sederhana tanpa kotakan/animasi -->
          <div class="hero-simple-features">
            <div v-for="(item, index) in features" :key="index" class="simple-feature-item">
              <h4 class="simple-feature-title">{{ item.title }}</h4>
              <p class="simple-feature-desc">{{ item.desc }}</p>
            </div>
          </div>
        </div>

        <!-- Sisi Kanan: Ilustrasi Game dengan Background Transparan -->
        <div class="hero-media">
          <img 
            :src="heroIllustration" 
            alt="GameDev Game Illustration - Character, Vehicle, and Weapons"
            class="hero-game-img"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  position: relative;
  width: 100%;
  background-color: #ffffff;
  overflow: hidden;
  padding: 2.5rem 0 3.5rem;
  box-sizing: border-box;
}

/* Shape persegi di kanan atas dengan warna #BBDEFB yang muncul sebagian */
.accent-shape-box {
  position: absolute;
  top: -60px;
  right: -60px;
  width: 420px;
  height: 380px;
  background-color: #BBDEFB;
  border-radius: 36px;
  transform: rotate(14deg);
  opacity: 0.8;
  z-index: 1;
  pointer-events: none;
}

.hero-container {
  position: relative;
  z-index: 2;
  width: 100%;
  padding: 0 2rem;
  box-sizing: border-box;
}

/* Layout Grid Kiri - Kanan */
.hero-main-grid {
  display: grid;
  grid-template-columns: 1.15fr 0.85fr;
  align-items: center;
  gap: 3rem;
}

/* Sisi Kiri */
.hero-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.hero-badge {
  display: inline-block;
  align-self: flex-start;
  font-size: 0.875rem;
  font-weight: 600;
  color: #00BCD4;
  background-color: rgba(0, 188, 212, 0.08);
  padding: 0.4rem 1.1rem;
  border-radius: 9999px;
  margin-bottom: 1.25rem;
  letter-spacing: 0.3px;
}

.hero-title {
  font-size: 2.85rem;
  line-height: 1.2;
  font-weight: 800;
  color: #0f172a;
  margin: 0 0 1.25rem 0;
  letter-spacing: -0.6px;
}

.highlight-text {
  color: #00BCD4;
}

.hero-description {
  font-size: 1.05rem;
  line-height: 1.7;
  color: #475569;
  margin: 0 0 2rem 0;
  max-width: 620px;
}

/* Tombol Aksi */
.hero-cta-group {
  display: flex;
  align-items: center;
  gap: 1.25rem;
  flex-wrap: wrap;
}

/* Button Contact Me: background putih, border #00BCD4 */
.btn-contact {
  background-color: #ffffff;
  color: #00BCD4;
  border: 2px solid #00BCD4;
  font-size: 0.95rem;
  font-weight: 600;
  padding: 0.75rem 2rem;
  border-radius: 8px;
  cursor: pointer;
  outline: none;
}

/* Button Join Now: background #00BCD4, teks putih */
.btn-join {
  background-color: #00BCD4;
  color: #ffffff;
  border: 2px solid #00BCD4;
  font-size: 0.95rem;
  font-weight: 600;
  padding: 0.75rem 2.2rem;
  border-radius: 8px;
  cursor: pointer;
  outline: none;
}

/* 3 Kelebihan Perusahaan: tepat di bawah button, horizontal, sederhana tanpa border/kotak/animasi */
.hero-simple-features {
  margin-top: 2.75rem;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.75rem;
  border: none;
  background: transparent;
  padding: 0;
}

.simple-feature-item {
  border: none;
  background: transparent;
  padding: 0;
  box-shadow: none;
}

.simple-feature-title {
  font-size: 0.95rem;
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 0.35rem 0;
  display: flex;
  align-items: center;
  gap: 0.4rem;
}

.simple-feature-title::before {
  content: '•';
  color: #00BCD4;
  font-size: 1.2rem;
  line-height: 1;
}

.simple-feature-desc {
  font-size: 0.85rem;
  line-height: 1.5;
  color: #64748b;
  margin: 0;
}

/* Sisi Kanan: Media Gambar dengan Latar Transparan murni */
.hero-media {
  display: flex;
  justify-content: center;
  align-items: center;
  background: transparent;
}

.hero-game-img {
  width: 100%;
  max-width: 540px;
  height: auto;
  display: block;
  object-fit: contain;
  background: transparent;
  border: none;
  box-shadow: none;
}

/* Responsive Breakpoints */
@media (max-width: 1024px) {
  .hero-main-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .hero-media {
    order: -1;
  }

  .hero-game-img {
    max-width: 420px;
  }

  .hero-title {
    font-size: 2.3rem;
  }

  .hero-simple-features {
    grid-template-columns: repeat(2, 1fr);
    margin-top: 2.25rem;
  }
}

@media (max-width: 640px) {
  .hero-container {
    padding: 0 1.25rem;
  }

  .accent-shape-box {
    width: 240px;
    height: 220px;
    top: -40px;
    right: -40px;
  }

  .hero-title {
    font-size: 1.85rem;
  }

  .hero-cta-group {
    flex-direction: column;
    width: 100%;
  }

  .btn-contact, .btn-join {
    width: 100%;
    text-align: center;
  }

  .hero-simple-features {
    grid-template-columns: 1fr;
    gap: 1.25rem;
    margin-top: 2rem;
  }
}
</style>
