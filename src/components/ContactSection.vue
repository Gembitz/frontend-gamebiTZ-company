<script setup>
import { reactive, ref } from 'vue'

// State form lokal (hanya tampilan UI sementara, tidak terhubung ke DB)
const formData = reactive({
  name: '',
  phone: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitted = ref(false)

const handleSubmit = () => {
  // Hanya simulasi feedback interaktif tampilan tanpa koneksi database
  isSubmitted.value = true
  setTimeout(() => {
    isSubmitted.value = false
    formData.name = ''
    formData.phone = ''
    formData.email = ''
    formData.subject = ''
    formData.message = ''
  }, 3000)
}

// Media sosial perusahaan
const socialLinks = [
  {
    name: 'Facebook',
    url: 'https://facebook.com',
    icon: `<path d="M18 2h-3a5 5 0 00-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 011-1h3z"/>`,
    color: '#1877f2'
  },
  {
    name: 'Instagram',
    url: 'https://instagram.com',
    icon: `<rect x="2" y="2" width="20" height="20" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1112.63 8 4 4 0 0116 11.37zm1.5-4.87h.01"/>`,
    color: '#e4405f'
  },
  {
    name: 'TikTok',
    url: 'https://tiktok.com',
    icon: `<path d="M9 12a4 4 0 104 4V4a5 5 0 005 5"/>`,
    color: '#000000'
  },
  {
    name: 'YouTube',
    url: 'https://youtube.com',
    icon: `<path d="M22.54 6.42a2.78 2.78 0 00-1.94-2C18.88 4 12 4 12 4s-6.88 0-8.6.46a2.78 2.78 0 00-1.94 2A29 29 0 001 11.75a29 29 0 00.46 5.33A2.78 2.78 0 003.4 19c1.72.46 8.6.46 8.6.46s6.88 0 8.6-.46a2.78 2.78 0 001.94-2 29 29 0 00.46-5.25 29 29 0 00-.46-5.33z"/><polygon points="9.75 15.02 15.5 11.75 9.75 8.48 9.75 15.02" fill="#ffffff"/>`,
    color: '#ff0000'
  }
]
</script>

<template>
  <section id="contact" class="contact-section">
    <div class="contact-container">
      <div class="contact-grid">
        
        <!-- SISI KIRI: Kontak Kami, Info Kontak Vertikal, Google Maps, & Social Media -->
        <div class="contact-info-col">
          <div class="header-badge">
            <span class="badge-dot"></span> Hubungi Kami
          </div>
          <h2 class="contact-title">Kontak Kami</h2>
          <p class="contact-desc">
            Punya pertanyaan seputar game kami, kolaborasi, atau ingin memesan merchandise? 
            Jangan ragu untuk menghubungi tim kami melalui kanal di bawah ini.
          </p>

          <!-- Informasi Kontak Tersusun Vertikal -->
          <div class="info-items-list">
            <!-- Nomor Telepon -->
            <div class="info-item">
              <div class="info-icon-box">
                <svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07 19.5 19.5 0 01-6-6 19.79 19.79 0 01-3.07-8.67A2 2 0 014.11 2h3a2 2 0 012 1.72 12.84 12.84 0 00.7 2.81 2 2 0 01-.45 2.11L8.09 9.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45 12.84 12.84 0 002.81.7A2 2 0 0122 16.92z"></path>
                </svg>
              </div>
              <div class="info-details">
                <span class="info-label">Nomor Telepon</span>
                <a href="tel:+62215550198" class="info-value">+62 (21) 555-0198</a>
              </div>
            </div>

            <!-- Email -->
            <div class="info-item">
              <div class="info-icon-box">
                <svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
                  <polyline points="22,6 12,13 2,6"></polyline>
                </svg>
              </div>
              <div class="info-details">
                <span class="info-label">Email Perusahaan</span>
                <a href="mailto:support@gamebitz.dev.id" class="info-value">support@gamedev.id</a>
              </div>
            </div>

            <!-- Website -->
            <div class="info-item">
              <div class="info-icon-box">
                <svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <circle cx="12" cy="12" r="10"></circle>
                  <line x1="2" y1="12" x2="22" y2="12"></line>
                  <path d="M12 2a15.3 15.3 0 014 10 15.3 15.3 0 01-4 10 15.3 15.3 0 01-4-10 15.3 15.3 0 014-10z"></path>
                </svg>
              </div>
              <div class="info-details">
                <span class="info-label">Website Resmi</span>
                <a href="https://www.gamebitz.dev.id" target="_blank" rel="noopener noreferrer" class="info-value">www.gamebitz.dev.id</a>
              </div>
            </div>

            <!-- Alamat -->
            <div class="info-item">
              <div class="info-icon-box">
                <svg viewBox="0 0 24 24" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"></path>
                  <circle cx="12" cy="10" r="3"></circle>
                </svg>
              </div>
              <div class="info-details">
                <span class="info-label">Alamat Studio</span>
                <p class="info-value mb-0">Jl. Cyber Tech Hub No. 88, Gedung GameDev Tower Lt. 12, Jakarta Selatan, 12930</p>
              </div>
            </div>
          </div>

          <!-- Google Maps Embed Terintegrasi di Bawah Alamat -->
          <div class="map-embed-wrapper">
            <iframe
              title="Google Maps Lokasi GameDev"
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3966.273893809828!2d106.80609907355438!3d-6.227574460986616!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e69f1495f1fddc9%3A0xfe3d872dbc2b760a!2sGoogle%20Indonesia!5e0!3m2!1sid!2sid!4v1791701308578!5m2!1sid!2sid"
              width="100%"
              height="220"
              style="border:0;"
              allowfullscreen=""
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
          </div>

          <!-- Social Media Icons di Bawah Google Maps -->
          <div class="social-links-box">
            <span class="social-heading">Ikuti Media Sosial Kami:</span>
            <div class="social-icons-group">
              <a
                v-for="social in socialLinks"
                :key="social.name"
                :href="social.url"
                target="_blank"
                rel="noopener noreferrer"
                class="social-icon-btn"
                :title="social.name"
                :style="{ '--hover-color': social.color }"
              >
                <svg
                  viewBox="0 0 24 24"
                  width="20"
                  height="20"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  class="social-svg"
                  v-html="social.icon"
                ></svg>
              </a>
            </div>
          </div>
        </div>

        <!-- SISI KANAN: Form "Kirimkan pesan kepada kami" -->
        <div class="contact-form-col">
          <div class="form-card">
            <h3 class="form-title">Kirimkan pesan kepada kami</h3>
            <p class="form-subtitle">
              Isi formulir di bawah ini dan tim support kami akan merespons dalam waktu 1x24 jam kerja.
            </p>

            <!-- Feedback Sukses Simulasi Tampilan -->
            <div v-if="isSubmitted" class="alert-success">
              ✓ Pesan Anda berhasil dikirim! Tim kami akan segera menghubungi Anda.
            </div>

            <form class="contact-form" @submit.prevent="handleSubmit">
              <!-- Field Nama -->
              <div class="form-group">
                <label for="name" class="form-label">Nama Lengkap</label>
                <input
                  id="name"
                  v-model="formData.name"
                  type="text"
                  class="form-input"
                  placeholder="Masukkan nama Anda..."
                  required
                />
              </div>

              <!-- Field No Telepon & Email Berdampingan -->
              <div class="form-row">
                <div class="form-group">
                  <label for="phone" class="form-label">Nomor Telepon</label>
                  <input
                    id="phone"
                    v-model="formData.phone"
                    type="tel"
                    class="form-input"
                    placeholder="Contoh: 081234567890"
                    required
                  />
                </div>
                <div class="form-group">
                  <label for="email" class="form-label">Email</label>
                  <input
                    id="email"
                    v-model="formData.email"
                    type="email"
                    class="form-input"
                    placeholder="nama@email.com"
                    required
                  />
                </div>
              </div>

              <!-- Field Subject -->
              <div class="form-group">
                <label for="subject" class="form-label">Subject</label>
                <input
                  id="subject"
                  v-model="formData.subject"
                  type="text"
                  class="form-input"
                  placeholder="Perihal pesan Anda (misal: Kerjasama Game, Pembelian Asset...)"
                  required
                />
              </div>

              <!-- Field Pesan -->
              <div class="form-group">
                <label for="message" class="form-label">Pesan</label>
                <textarea
                  id="message"
                  v-model="formData.message"
                  rows="5"
                  class="form-textarea"
                  placeholder="Tuliskan pesan atau detail pertanyaan Anda di sini..."
                  required
                ></textarea>
              </div>

              <!-- Tombol Kirim -->
              <div class="form-action">
                <button type="submit" class="btn-submit">
                  <span>Kirim Pesan</span>
                  <svg viewBox="0 0 24 24" width="18" height="18" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <line x1="22" y1="2" x2="11" y2="13"></line>
                    <polygon points="22 2 15 22 11 13 2 9 22 2"></polygon>
                  </svg>
                </button>
              </div>
            </form>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  width: 100%;
  background-color: #f8fafc;
  padding: 3.5rem 0 4rem;
  box-sizing: border-box;
}

.contact-container {
  max-width: 1140px;
  margin: 0 auto;
  padding: 0 1.5rem;
  box-sizing: border-box;
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2.5rem;
  align-items: start;
}

/* =========================================
   SISI KIRI: INFO KONTAK, MAPS, SOCIAL MEDIA
   ========================================= */
.contact-info-col {
  display: flex;
  flex-direction: column;
}

.header-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.8px;
  color: #00BCD4;
  margin-bottom: 0.4rem;
}

.badge-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background-color: #00BCD4;
}

.contact-title {
  font-size: 1.85rem;
  font-weight: 800;
  color: #0f172a;
  margin: 0 0 0.5rem 0;
  letter-spacing: -0.4px;
}

.contact-desc {
  font-size: 0.9rem;
  line-height: 1.6;
  color: #64748b;
  margin: 0 0 1.5rem 0;
}

/* List Item Kontak Vertikal Compact */
.info-items-list {
  display: flex;
  flex-direction: column;
  gap: 0.85rem;
  margin-bottom: 1.5rem;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 0.85rem;
}

/* Warna icon info box disesuaikan dengan #B7DFFF */
.info-icon-box {
  width: 36px;
  height: 36px;
  border-radius: 8px;
  background-color: rgba(183, 223, 255, 0.28);
  color: #0284c7;
  border: 1.5px solid #B7DFFF;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.info-icon-box svg {
  stroke: #0284c7;
}

.info-details {
  display: flex;
  flex-direction: column;
}

.info-label {
  font-size: 0.725rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  color: #94a3b8;
  margin-bottom: 0.1rem;
}

.info-value {
  font-size: 0.9rem;
  font-weight: 600;
  color: #1e293b;
  text-decoration: none;
  line-height: 1.4;
  transition: color 0.2s ease;
}

a.info-value:hover {
  color: #0284c7;
}

.mb-0 {
  margin: 0;
}

/* Google Maps Embed Minimalis */
.map-embed-wrapper {
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.04);
  border: 1px solid #e2e8f0;
  margin-bottom: 1.35rem;
  background-color: #ffffff;
}

.map-embed-wrapper iframe {
  display: block;
  height: 170px;
}

/* Social Media Section */
.social-links-box {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.social-heading {
  font-size: 0.825rem;
  font-weight: 600;
  color: #64748b;
}

.social-icons-group {
  display: flex;
  align-items: center;
  gap: 0.65rem;
}

.social-icon-btn {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background-color: #ffffff;
  color: #0284c7;
  border: 1.5px solid #B7DFFF;
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.03);
}

.social-icon-btn:hover {
  color: #ffffff;
  background-color: var(--hover-color, #0284c7);
  border-color: var(--hover-color, #0284c7);
  transform: translateY(-2px);
  box-shadow: 0 6px 14px rgba(0, 0, 0, 0.12);
}

/* =========================================
   SISI KANAN: FORM PESAN MINIMALIS
   ========================================= */
.contact-form-col {
  width: 100%;
}

.form-card {
  background-color: #ffffff;
  border-radius: 16px;
  padding: 2rem 2rem 2.25rem;
  box-shadow: 0 4px 20px -2px rgba(0, 0, 0, 0.05);
  border: 1px solid #e2e8f0;
}

.form-title {
  font-size: 1.35rem;
  font-weight: 800;
  color: #0f172a;
  margin: 0 0 0.35rem 0;
  letter-spacing: -0.3px;
}

.form-subtitle {
  font-size: 0.875rem;
  color: #64748b;
  line-height: 1.5;
  margin: 0 0 1.35rem 0;
}

.alert-success {
  background-color: #ecfdf5;
  color: #059669;
  border: 1px solid #a7f3d0;
  padding: 0.65rem 1rem;
  border-radius: 8px;
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 1.25rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}

.form-label {
  font-size: 0.825rem;
  font-weight: 600;
  color: #334155;
}

.form-input, .form-textarea {
  width: 100%;
  padding: 0.65rem 0.85rem;
  border-radius: 8px;
  border: 1.5px solid #e2e8f0;
  background-color: #f8fafc;
  color: #0f172a;
  font-size: 0.875rem;
  font-family: inherit;
  box-sizing: border-box;
  outline: none;
  transition: all 0.2s ease;
}

.form-input:focus, .form-textarea:focus {
  background-color: #ffffff;
  border-color: #00BCD4;
  box-shadow: 0 0 0 3px rgba(0, 188, 212, 0.12);
}

.form-textarea {
  resize: vertical;
  min-height: 95px;
}

.form-action {
  margin-top: 0.25rem;
}

.btn-submit {
  width: 100%;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  background-color: #00BCD4;
  color: #ffffff;
  border: none;
  font-size: 0.925rem;
  font-weight: 700;
  padding: 0.75rem 1.75rem;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.25s ease;
  box-shadow: 0 4px 12px rgba(0, 188, 212, 0.25);
  outline: none;
}

.btn-submit:hover {
  background-color: #00acc1;
  transform: translateY(-2px);
  box-shadow: 0 6px 16px rgba(0, 188, 212, 0.35);
}

.btn-submit:active {
  transform: translateY(0);
}

/* Responsive Breakpoints */
@media (max-width: 900px) {
  .contact-grid {
    grid-template-columns: 1fr;
    gap: 2.25rem;
  }

  .form-card {
    padding: 1.75rem 1.25rem;
  }

  .social-links-box {
    flex-direction: column;
    align-items: flex-start;
  }
}

@media (max-width: 600px) {
  .contact-section {
    padding: 2.5rem 0 3rem;
  }

  .form-row {
    grid-template-columns: 1fr;
  }

  .contact-title {
    font-size: 1.6rem;
  }
}
</style>
