<template>
    <q-page>

        <!-- header section -->
        <div style="padding: 80px 48px 64px; border-bottom: 1px solid #EBEBEB;">
          <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; font-weight: 500; letter-spacing: 0.12em; color: #6B6B6B; text-transform: uppercase; margin-bottom: 24px;">
            Tentang Aku
          </div>
          <h1 style="font-family: 'Plus Jakarta Sans', sans-serif; font-size: 48px; font-weight: 500; line-height: 1.1; margin: 0 0 24px; max-width: 560px;">
            Digital Creative Multimedia & Computer Technology.
          </h1>
          <p style="font-family: 'Geist Mono', sans-serif; font-size: 16px; line-height: 1.7; color: #6B6B6B; max-width: 520px; margin: 0;">
            A Bachelor of Applied Science in Digital Creative Multimedia graduate from Telkom University, with a prior background in Computer Technology (Associate Degree) and hands- on experience in the field of information technology. During my studies, I contributed to research and development projects in the areas of IoT and Embedded Systems, involving design, implementation, and data analysis. I also possess strong skills in UI/UX design using Figma. I am passionate and eager to contribute professionally in the fields of smart technology and design.
          </p>
        </div>

        <!-- profile section -->
        <div style="padding: 64px 48px; border-bottom: 1px solid #EBEBEB;">
          <div style="display: flex; gap: 48px; align-items: flex-start; flex-wrap: wrap;">

            <!-- avatar -->
            <div style="flex-shrink: 0;">
              <q-avatar
                size="120px"
                color="dark"
                text-color="white"
                style="font-family: 'Plus Jakarta Sans', sans-serif; font-size: 48px;"
              >
                A
              </q-avatar>
            </div>

            <!-- info -->
            <div style="flex: 1; min-width: 280px;">
              <div style="font-family: 'Plus Jakarta Sans', sans-serif; font-size: 28px; font-weight: 500; margin-bottom: 8px;">
                Andika
              </div>
              <div style="font-family: 'Geist Mono', sans-serif; font-size: 13px; color: #6B6B6B; margin-bottom: 24px; letter-spacing: 0.05em;">
                UI/UX Designer · MagangHub Kemenaker
              </div>
              <p style="font-family: 'Geist Mono', sans-serif; font-size: 15px; line-height: 1.7; color: #4A4A4A; margin: 0;">
                UI/UX Designer dengan Figma dan mempelajari Frontend Development menggunakan Quasar Framework.
              </p>
            </div>

          </div>
        </div>

        <!-- pengalaman section -->
        <div style="padding: 64px 48px;">
          <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; font-weight: 500; letter-spacing: 0.12em; color: #6B6B6B; text-transform: uppercase; margin-bottom: 48px;">
            Pengalaman
          </div>

          <div style="max-width: 600px;">
            <div
              v-for="(exp, index) in pengalaman"
              :key="exp.judul"
              style="display: flex; gap: 32px; margin-bottom: 48px;"
            >
              <!-- timelin indikator -->
              <div style="display: flex; flex-direction: column; align-items: center;">
                <div style="width: 10px; height: 10px; border-radius: 50%; background: #2D2D2D; flex-shrink: 0; margin-top: 6px;"></div>
                <div
                  v-if="index < pengalaman.length - 1"
                  style="width: 1px; background: #EBEBEB; flex: 1; margin-top: 8px;"
                >
                </div>
              </div>

              <!-- content -->
              <div style="flex: 1; padding-bottom: 16px;">
                <div style="font-family: 'Geist Mono', sans-serif; font-size: 12px; letter-spacing: 0.08em; color: #C9A96E; text-transform: uppercase; margin-bottom: 8px;">
                  {{ exp.waktu }}
                </div>
                <div style="font-family: 'Plus Jakarta Sans', sans-serif; font-size: 20px; margin-bottom: 8px;">
                  {{ exp.judul }}
                </div>
                <p style="font-family: 'Geist Mono', sans-serif; font-size: 14px; color: #6B6B6B; line-height: 1.6; margin: 0;">
                  {{ exp.deskripsi }}
                </p>
              </div>

            </div>
          </div>
        </div>

    </q-page>
</template>

<script setup>
const pengalaman =[
    {
        judul: 'UI/UX Designer Intern - MagangHUB Kemenaker',
        waktu: '2024 - Sekarang',
        deskripsi: 'Mengerjakan task UI/UX design menggunakan Figma, serta mempelajari Frontend Development dengan Quasar.'
    },
    {
        judul: 'UI/UX Designer',
        waktu: 'Des 2023 - Des 2024',
        deskripsi: 'Mengerjakan proyek desain seperti dashboard untuk monitoring sistem IoT, Aplikasi VR termasuk pembuatan wireframe, HiFi Design, Prototype, Testing.'
    },
    {
        judul: 'IoT Hardware ngineer',
        waktu: '2022 - 2023',
        deskripsi: 'Membantu penelitian di bidang IoT dan Embedded Systems, termasuk perancangan, implementasi, dan analisis data.'
    }
]
</script>
