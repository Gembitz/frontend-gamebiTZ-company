<script setup>
import tencentLogo from '../assets/tencent_logo.png'

// Daftar 14 mitra lengkap (bisa menggunakan image file ataupun SVG)
const partners = [
  {
    name: 'Supercell',
    image: 'https://www.logo.wine/a/logo/Supercell_(video_game_company)/Supercell_(video_game_company)-Logo.wine.svg'
  },
  {
    name: 'Garena',
    image: 'https://i.pinimg.com/1200x/55/91/ff/5591ff7e7c75843c885c8a0a4957f167.jpg'
  },
  {
    name: 'Moonton',
    image: 'https://zonalogo.com/assets/moonton-logo-png-svg.webp?asset=2108&w=400'
  },
  {
    name: 'Tencent',
    image: tencentLogo // Logo kustom dari file / URL gambar
  },
  {
    name: 'Google',
    image: 'https://static.freepnglogo.com/images/all_img/google-logo-2025-6ffb.png'
  },
  {
    name: 'Meta',
    image: 'https://freepngimg.com/thumb/meta/123016-meta-logo.png'
  },
  {
    name: 'Gameloft',
    image: 'https://images.seeklogo.com/logo-png/17/2/gameloft-logo-png_seeklogo-177060.png'
  },
  {
    name: 'Sony PlayStation',
    image: 'https://www.logo.wine/a/logo/PlayStation/PlayStation-Logo.wine.svg'
  },
  {
    name: 'Microsoft',
    image: 'https://www.freepnglogos.com/uploads/microsoft-window-logo-emblem-0.png'
  },
  {
    name: 'Nintendo',
    image: 'https://images.seeklogo.com/logo-png/9/2/nintendo-logo-png_seeklogo-99658.png'
  },
  {
    name: 'NetEase',
    image: 'https://images.seeklogo.com/logo-png/53/1/netease-games-logo-png_seeklogo-538621.png'
  },
  {
    name: 'EA (Electronic Arts)',
    image: 'https://wp.logos-download.com/wp-content/uploads/2016/11/EA_logo_logotype-700x303.png'
  },
  {
    name: 'Epic Games',
    image: 'https://upload.wikimedia.org/wikipedia/commons/a/a7/Epic_Games_logo.png?utm_source=commons.wikimedia.org&utm_campaign=index&utm_content=thumbnail_unscaled&_=20180404191303'
  },
  {
    name: 'Bandai Namco',
    image: 'https://download.logo.wine/logo/Bandai_Namco_Entertainment/Bandai_Namco_Entertainment-Logo.wine.png'
  }
]
</script>

<template>
  <section class="partner-ticker-section">
    <div class="partner-track-container">
      <!-- Infinite Marquee Track: Bergerak perlahan dari kiri ke kanan -->
      <div class="partner-marquee">
        <!-- Set Pertama -->
        <div class="partner-group">
          <div 
            v-for="partner in partners" 
            :key="'set1-' + partner.name" 
            class="partner-logo-item"
            :title="partner.name"
          >
            <div class="logo-box">
              <!-- Render Gambar PNG/JPG/URL jika ada -->
              <img 
                v-if="partner.image" 
                :src="partner.image" 
                :alt="partner.name" 
                class="brand-icon-img"
              />
              <!-- Render SVG jika memakai format SVG -->
              <svg 
                v-else
                :viewBox="partner.viewBox" 
                class="brand-icon"
                v-html="partner.svg"
              ></svg>
            </div>
          </div>
        </div>

        <!-- Set Kedua untuk Endless Continuous Loop -->
        <div class="partner-group" aria-hidden="true">
          <div 
            v-for="partner in partners" 
            :key="'set2-' + partner.name" 
            class="partner-logo-item"
            :title="partner.name"
          >
            <div class="logo-box">
              <img 
                v-if="partner.image" 
                :src="partner.image" 
                :alt="partner.name" 
                class="brand-icon-img"
              />
              <svg 
                v-else
                :viewBox="partner.viewBox" 
                class="brand-icon"
                v-html="partner.svg"
              ></svg>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.partner-ticker-section {
  width: 100%;
  background-color: #DAEEFF;
  border-top: 1px solid rgba(0, 0, 0, 0.05);
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
  padding: 1.5rem 0;
  overflow: hidden;
  box-sizing: border-box;
}

.partner-track-container {
  width: 100%;
  overflow: hidden;
  position: relative;
  /* Fade lembut di tepi kiri dan kanan */
  mask-image: linear-gradient(
    to right,
    transparent 0%,
    rgba(0, 0, 0, 1) 5%,
    rgba(0, 0, 0, 1) 95%,
    transparent 100%
  );
  -webkit-mask-image: linear-gradient(
    to right,
    transparent 0%,
    rgba(0, 0, 0, 1) 5%,
    rgba(0, 0, 0, 1) 95%,
    transparent 100%
  );
}

.partner-marquee {
  display: flex;
  width: max-content;
  /* Bergerak perlahan dari kiri ke kanan */
  animation: scrollLeftToRight 36s linear infinite;
  will-change: transform;
}

/* Berhenti berjalan ketika disentuh/hover */
.partner-marquee:hover {
  animation-play-state: paused;
}

.partner-group {
  display: flex;
  align-items: center;
  gap: 3.5rem;
  padding-right: 3.5rem;
}

.partner-logo-item {
  display: flex;
  align-items: center;
  cursor: pointer;
  user-select: none;
}

/* Kotak logo partner murni */
.logo-box {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.65rem 1.4rem;
  border-radius: 12px;
  background-color: transparent;
  /* Default: Abu-abu (grayscale) */
  filter: grayscale(100%) opacity(40%);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.brand-icon {
  width: 44px;
  height: 44px;
  display: block;
  fill: currentColor;
  flex-shrink: 0;
  transition: transform 0.3s ease;
}

.brand-icon-img {
  width: auto;
  height: 44px;
  max-width: 80px;
  display: block;
  object-fit: contain;
  flex-shrink: 0;
  transition: transform 0.3s ease;
}

/* Hover: Warna kembali cerah, kontras, dan timbul */
.partner-logo-item:hover .logo-box {
  filter: grayscale(0%) opacity(100%);
  background-color: #ffffff;
  box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1);
  transform: translateY(-3px) scale(1.15);
}

.partner-logo-item:hover .brand-icon {
  transform: scale(1.05);
}

/* Gerakan continuous dari kiri ke kanan */
@keyframes scrollLeftToRight {
  0% {
    transform: translateX(-50%);
  }
  100% {
    transform: translateX(0%);
  }
}

@media (max-width: 768px) {
  .partner-ticker-section {
    padding: 1.1rem 0;
  }

  .partner-group {
    gap: 2.2rem;
    padding-right: 2.2rem;
  }

  .brand-icon {
    width: 34px;
    height: 34px;
  }
}
</style>
