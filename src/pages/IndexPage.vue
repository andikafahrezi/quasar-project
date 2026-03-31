<template>
  <q-page>

    <!-- hero section -->
    <div style="padding: 80px 48px 64px; border-bottom: 1px solid #ebebeb;">
      <div style="max-width: 640px;">
        <div style="font-family: 'Geist Mono', sans-serif; font-size: 13px; letter-spacing: 0.1rem; color: #6b6b6b; text-transform: uppercase; margin-bottom: 24px;">
          UI/UX Designer & Frontend Learner
        </div>
        <h1 style="font-family: 'Plus Jakarta Sans', serif; font-size: 48px; font-weight: 500; line-height: 1.1; margin: 0 0 24px;">
          Halo, Aku Andika 👋
        </h1>
        <p style="font-family: 'Geist Mono', sans-serif; font-size: 16px; line-height: 1.7; color: #6b6b6b; margin: 0 0 32px;">
          Sedang belajar Frontend Development. Saat ini magang dari program MagangHub Kemenaker.
        </p>
        <div style="display: flex; gap: 12px;">
          <q-btn
            to="/contact"
            label="Hubungi Aku"
            color="dark"
            unelevated
            style="border-radius: 8px; font-size: 13px; padding: 10px 24px;"
          />
          <q-btn
            to="/about"
            label="Tentang Aku"
            flat
            color="dark"
            style="border-radius: 8px; font-size: 13px; padding: 10px 24px;"
          />
        </div>
      </div>
    </div>

    <!-- skills section -->
    <div style="padding: 64px 48px; border-bottom: 1px solid #ebebeb;">
      <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; letter-spacing: 0.12rem; color: #6b6b6b; text-transform: uppercase; margin-bottom: 32px;">
        Skills
      </div>
      <div style="display: flex; flex-wrap: wrap; gap: 10px;">
        <div
          v-for="skill in skills"
          :key="skill"
          style="font-family: 'Geist Mono', sans-serif; padding: 8px 16px; border: 1px solid #2d2d2d; border-radius: 100px; font-size: 13px;"
        >
          {{ skill }}
        </div>
      </div>
    </div>

    <!-- projects section -->
    <div style="padding: 64px 48px;">
      <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; letter-spacing: 0.12em; color: #6B6B6B; text-transform: uppercase; margin-bottom: 32px;">
        Projects
      </div>
      <div class="row q-gutter-md">
        <div
          v-for="project in projects"
          :key="project.nama"
          class="col-12 col-md-4"
        >
          <div
            style="padding: 32px; border: 1px solid #EBEBEB; border-radius: 12px; height: 100%; background: white; cursor: pointer; transition: border-color 0.2s;"
            @mouseenter="e => e.currentTarget.style.borderColor = '#2D2D2D'"
            @mouseleave="e => e.currentTarget.style.borderColor = '#ebebeb'"
          >
            <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; color: #C9A96E; margin-bottom: 12px;">
              {{ project.kategori }}
            </div>
            <div style="font-family: 'Plus Jakarta Sans', sans-serif; font-size: 22px; font-weight: 600; margin-bottom: 12px; line-height: 1.3;">
              {{ project.nama }}
            </div>
            <p style="font-family: 'Geist Mono', sans-serif; font-size: 14px; color: #6B6B6B; line-height: 1.6; margin: 0;">
              {{ project.deskripsi }}
            </p>
          </div>
        </div>
      </div>
    </div>

  </q-page>
</template>

<script setup>
const skills = [
  'Figma',
  'UI/UX Design',
  'HTML',
  'CSS',
  'JavaScript',
  'Vue',
  'Quasar'
]

const projects = [
  {
    nama: 'Portofolio Website',
    kategori: 'UI/UX Design',
    deskripsi: 'Desain portfolio pribadi dengan minimal editorial.'
  },
  {
    nama: 'Dashboard App',
    kategori: 'Frontend',
    deskripsi: 'Dashboard data visualisasi menggunakan Quasar.'
  },
  {
    nama: 'Smart Mannequin',
    kategori: 'IoT Smart System Research',
    deskripsi: 'Prototipe dummy manekin dengan sensor untuk mengukur keergonomisan kendaraan tempur berbasis IoT'
  }
]
</script>
