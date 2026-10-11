<script setup>
// Props image agar user bisa memasukkan gambarnya sendiri nanti
defineProps({
  aboutImage: {
    type: String,
    default: 'https://ids.ac.id/wp-content/uploads/2020/12/developer-game-1024x439.jpeg' // User bisa mengisinya lewat props atau import lokal
  }
})

// Data 3 kartu poin di sebelah kanan gambar (Disesuaikan dengan industri game GamebiTZ)
const featurePoints = [
  {
    title: 'Kualitas Gameplay Terbaik',
    type: 'check',
    bgColor: '#dbeafe', // soft blue badge
    iconColor: '#2563eb'
  },
  {
    title: 'Performa Tinggi & Responsif',
    type: 'speed',
    bgColor: '#f3e8ff', // soft purple badge
    iconColor: '#9333ea'
  },
  {
    title: 'Inovasi & Kreativitas Tanpa Batas',
    type: 'bulb',
    bgColor: '#fef3c7', // soft yellow/orange badge
    iconColor: '#f59e0b'
  }
]
</script>

<template>
  <section id="about" class="about-section">
    <!-- Background diagonal soft accent -->
    <div class="bg-diagonal-accent" aria-hidden="true"></div>

    <div class="about-container">
      <!-- Grid Utama: Kiri (Badge Belah Ketupat & Deskripsi), Kanan (Gambar & 3 Card Poin) -->
      <div class="about-grid">
        
        <!-- SISI KIRI: Elemen Belah Ketupat About US & Teks -->
        <div class="about-left-col">
          <!-- Area Dekorasi Geometris Berlapis -->
          <div class="rhombus-decorative-wrapper">
            <!-- Ikon Bulat YouTube / Play di sudut atas lingkaran garis -->
            <div class="circle-icon-badge badge-youtube">
              <svg viewBox="0 0 24 24" width="18" height="18" fill="currentColor">
                <path d="M10 15l5-3-5-3v6z"/>
              </svg>
            </div>

            <!-- Ikon Bulat Kecil Ungu (Email / Chat) -->
            <div class="circle-icon-badge badge-purple-mail">
              <svg viewBox="0 0 24 24" width="10" height="10" fill="currentColor">
                <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
              </svg>
            </div>

            <!-- Ikon Bulat Kecil Biru (Bintang) -->
            <div class="circle-icon-badge badge-blue-star">
              <svg viewBox="0 0 24 24" width="10" height="10" fill="currentColor">
                <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon>
              </svg>
            </div>

            <!-- Garis kurva luar dekoratif -->
            <div class="outer-wireframe wireframe-1"></div>
            <div class="outer-wireframe wireframe-2"></div>

            <!-- Belah Ketupat Lapis Transparan Tipis di belakang -->
            <div class="rhombus-layer rhombus-layer-outer"></div>

            <!-- Belah Ketupat Utama Solid Biru (#2196F3) -->
            <div class="rhombus-layer rhombus-main-blue">
              <div class="rhombus-inner-text">
                <span class="rhombus-title">About</span>
                <span class="rhombus-subtitle">US</span>
              </div>
            </div>

            <!-- Pin / Location Icon Bulat Ungu di sudut kiri bawah belah ketupat -->
            <div class="circle-icon-badge badge-purple-pin">
              <svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor">
                <path d="M16 12V4h1V2H7v2h1v8l-2 2v2h5.2v6h1.6v-6H18v-2l-2-2z"/>
              </svg>
            </div>
          </div>

          <!-- Teks Deskripsi di bawah / menyatu dengan layout kiri -->
          <div class="about-text-content">
            <h2 class="about-heading">Menciptakan Pengalaman Bermain yang Imersif & Berkesan</h2>
            <p class="about-paragraph">
              GamebiTZ berdedikasi membangun dunia interaktif melalui perpaduan seni visual memukau, 
              cerita mendalam, dan teknologi mesin game terkini. Kami terus berinovasi bersama komunitas 
              dan mitra global untuk menghadirkan hiburan digital berkelas dunia.
            </p>
          </div>
        </div>

        <!-- SISI KANAN: Gambar dengan Grid Grid-Line & 3 Kartu Mengambang -->
        <div class="about-right-col">
          <div class="image-with-overlays-container">
            <!-- Frame Gambar Utama -->
            <div class="about-image-frame">
              <!-- Jika user memasukkan prop gambar -->
              <img 
                v-if="aboutImage" 
                :src="aboutImage" 
                alt="About us visual" 
                class="actual-image"
              />
              <!-- Placeholder bersih siap pakai jika belum ada gambar -->
              <div v-else class="image-placeholder">
                <div class="placeholder-icon">
                  <svg viewBox="0 0 24 24" width="48" height="48" fill="none" stroke="#94a3b8" stroke-width="1.5">
                    <rect x="3" y="3" width="18" height="18" rx="2" ry="2"></rect>
                    <circle cx="8.5" cy="8.5" r="1.5"></circle>
                    <polyline points="21 15 16 10 5 21"></polyline>
                  </svg>
                  <span>Silakan masukkan gambar</span>
                </div>
              </div>

              <!-- Overlay Grid Titik & Garis Plus (+) seperti di desain -->
              <div class="grid-cross-overlay" aria-hidden="true">
                <div v-for="row in 3" :key="'r-'+row" class="grid-cross-row">
                  <span v-for="col in 4" :key="'c-'+col" class="cross-mark">+</span>
                </div>
              </div>
            </div>

            <!-- 3 Floating Feature Badges di sisi kanan (overlap sebagian ke gambar) -->
            <div class="floating-features-stack">
              <div 
                v-for="(point, idx) in featurePoints" 
                :key="idx" 
                class="floating-card"
              >
                <!-- Badge Ikon Bulat -->
                <div 
                  class="card-icon-badge" 
                  :style="{ backgroundColor: point.bgColor, color: point.iconColor }"
                >
                  <!-- Check Icon -->
                  <svg v-if="point.type === 'check'" viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <circle cx="12" cy="12" r="9"></circle>
                    <polyline points="9 12 11 14 15 10"></polyline>
                  </svg>

                  <!-- Speed / Tachometer Icon -->
                  <svg v-else-if="point.type === 'speed'" viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <circle cx="12" cy="12" r="9"></circle>
                    <polyline points="12 12 14 8"></polyline>
                    <path d="M7 16a6 6 0 0110 0"></path>
                  </svg>

                  <!-- Lightbulb / Idea Icon -->
                  <svg v-else-if="point.type === 'bulb'" viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M9 18h6"></path>
                    <path d="M10 22h4"></path>
                    <path d="M12 2v2"></path>
                    <path d="M12 6a5 5 0 00-5 5c0 1.5.8 2.8 2 3.6V16h6v-1.4c1.2-.8 2-2.1 2-3.6a5 5 0 00-5-5z"></path>
                  </svg>
                </div>

                <!-- Teks Kartu -->
                <span class="card-label">{{ point.title }}</span>
              </div>
            </div>

          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  position: relative;
  width: 100%;
  background-color: #ffffff;
  padding: 5.5rem 0 6rem;
  overflow: hidden;
  box-sizing: border-box;
}

/* Background aksen diagonal lembut di sudut kanan atas (#edf6fd) */
.bg-diagonal-accent {
  position: absolute;
  top: 0;
  right: 0;
  width: 55%;
  height: 100%;
  background-color: #f1f8fe;
  clip-path: polygon(25% 0%, 100% 0%, 100% 100%, 0% 100%);
  z-index: 1;
  pointer-events: none;
}

.about-container {
  position: relative;
  z-index: 2;
  width: 100%;
  padding: 0 2rem;
  box-sizing: border-box;
}

/* Layout Grid 2 Kolom */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  align-items: center;
  gap: 3.5rem;
}

/* =========================================
   SISI KIRI: BELAH KETUPAT & DESKRIPSI
   ========================================= */
.about-left-col {
  display: flex;
  flex-direction: column;
  position: relative;
}

.rhombus-decorative-wrapper {
  position: relative;
  width: 250px;
  height: 250px;
  margin-bottom: 2rem;
}

/* Belah Ketupat Utama Biru (#2196F3) */
.rhombus-layer {
  position: absolute;
  top: 40px;
  left: 40px;
  width: 155px;
  height: 155px;
  border-radius: 28px;
  transform: rotate(45deg);
  display: flex;
  align-items: center;
  justify-content: center;
}

.rhombus-layer-outer {
  background-color: rgba(33, 150, 243, 0.22);
  top: 28px;
  left: 28px;
  width: 180px;
  height: 180px;
  border-radius: 36px;
  z-index: 2;
}

.rhombus-main-blue {
  background: linear-gradient(135deg, #2196F3 0%, #1e88e5 100%);
  box-shadow: 0 12px 30px rgba(33, 150, 243, 0.35);
  z-index: 4;
}

/* Teks dalam Belah Ketupat (dikembalikan rotasinya agar lurus) */
.rhombus-inner-text {
  transform: rotate(-45deg);
  text-align: center;
  color: #ffffff;
  user-select: none;
}

.rhombus-title {
  display: block;
  font-size: 1.85rem;
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -0.5px;
}

.rhombus-subtitle {
  display: block;
  font-size: 1.6rem;
  font-weight: 800;
  letter-spacing: 1.5px;
}

/* Garis kawat luar melengkung tipis */
.outer-wireframe {
  position: absolute;
  border: 1.5px solid rgba(33, 150, 243, 0.35);
  border-radius: 48px;
  transform: rotate(45deg);
  pointer-events: none;
}

.wireframe-1 {
  top: 15px;
  left: 15px;
  width: 205px;
  height: 205px;
  z-index: 1;
}

.wireframe-2 {
  top: 2px;
  left: 2px;
  width: 232px;
  height: 232px;
  border-color: rgba(33, 150, 243, 0.18);
  border-radius: 54px;
  z-index: 0;
}

/* Bulatan Ikon-Ikon Kecil */
.circle-icon-badge {
  position: absolute;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #ffffff;
  z-index: 6;
}

/* Tombol YouTube Cyan di sudut atas */
.badge-youtube {
  top: -12px;
  left: 100px;
  width: 38px;
  height: 38px;
  background-color: #00BCD4;
  box-shadow: 0 4px 12px rgba(0, 188, 212, 0.35);
}

/* Ikon Email Ungu kecil */
.badge-purple-mail {
  top: 55px;
  right: -5px;
  width: 22px;
  height: 22px;
  background-color: #8b5cf6;
}

/* Ikon Bintang Biru kecil */
.badge-blue-star {
  top: 105px;
  right: -14px;
  width: 22px;
  height: 22px;
  background-color: #2196F3;
}

/* Ikon Pin Lokasi Ungu di kiri bawah belah ketupat */
.badge-purple-pin {
  bottom: 24px;
  left: 95px;
  width: 36px;
  height: 36px;
  background-color: #7c3aed;
  box-shadow: 0 4px 12px rgba(124, 58, 237, 0.35);
}

/* Konten Teks Kiri */
.about-text-content {
  max-width: 460px;
}

.about-heading {
  font-size: 1.45rem;
  font-weight: 700;
  color: #0f172a;
  line-height: 1.35;
  margin: 0 0 0.85rem 0;
}

.about-paragraph {
  font-size: 0.95rem;
  line-height: 1.65;
  color: #64748b;
  margin: 0;
}

/* =========================================
   SISI KANAN: FRAME GAMBAR & 3 FLOATING CARDS
   ========================================= */
.about-right-col {
  position: relative;
  display: flex;
  justify-content: center;
}

.image-with-overlays-container {
  position: relative;
  width: 100%;
  max-width: 580px;
}

/* Frame Gambar */
.about-image-frame {
  position: relative;
  width: 78%;
  aspect-ratio: 4 / 3;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 15px 35px -10px rgba(0, 0, 0, 0.15);
  background-color: #e2e8f0;
}

.actual-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #e2e8f0 0%, #cbd5e1 100%);
}

.placeholder-icon {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  color: #64748b;
  font-size: 0.9rem;
  font-weight: 500;
}

/* Grid Cross Tanda Plus (+) Transparan di atas Gambar */
.grid-cross-overlay {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  padding: 1.5rem;
  pointer-events: none;
}

.grid-cross-row {
  display: flex;
  justify-content: space-around;
}

.cross-mark {
  color: rgba(255, 255, 255, 0.65);
  font-size: 1.25rem;
  font-weight: 300;
  user-select: none;
  text-shadow: 0 0 2px rgba(0, 0, 0, 0.4);
}

/* 3 Kartu Mengambang di Sebelah Kanan (Menimpa Sebagian Gambar) */
.floating-features-stack {
  position: absolute;
  top: 50%;
  right: 0;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  gap: 1.15rem;
  width: 52%;
  z-index: 10;
}

/* Kartu Biru Muda Solid (#BBDEFB / Soft Blue) */
.floating-card {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 0.9rem 1.4rem;
  background-color: #c7e5ff;
  border-radius: 8px;
  box-shadow: 0 8px 20px -4px rgba(33, 150, 243, 0.2);
  transition: transform 0.25s ease;
}

.floating-card:hover {
  transform: translateX(4px);
}

.card-icon-badge {
  width: 34px;
  height: 34px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  background-color: #ffffff;
}

.card-label {
  font-size: 1rem;
  font-weight: 700;
  color: #0f172a;
  white-space: nowrap;
}

/* Responsive Breakpoints */
@media (max-width: 1024px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 4rem;
  }

  .about-text-content {
    max-width: 100%;
  }

  .image-with-overlays-container {
    max-width: 520px;
    margin: 0 auto;
  }
}

@media (max-width: 640px) {
  .about-section {
    padding: 3.5rem 0 4rem;
  }

  .about-container {
    padding: 0 1.25rem;
  }

  .rhombus-decorative-wrapper {
    width: 200px;
    height: 200px;
  }

  .rhombus-layer {
    width: 120px;
    height: 120px;
    top: 30px;
    left: 30px;
  }

  .rhombus-layer-outer {
    width: 140px;
    height: 140px;
    top: 20px;
    left: 20px;
  }

  .wireframe-1 {
    width: 160px;
    height: 160px;
  }

  .wireframe-2 {
    width: 180px;
    height: 180px;
  }

  .badge-youtube {
    left: 70px;
  }

  .badge-purple-pin {
    left: 70px;
  }

  .about-image-frame {
    width: 90%;
  }

  .floating-features-stack {
    position: static;
    transform: none;
    width: 100%;
    margin-top: 1.5rem;
  }

  .card-label {
    font-size: 0.9rem;
  }
}
</style>
