<!-- <script>
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'ContactPage',
    data() {
        return {
        form: {
            nama: '',
            email: '',
            pesan: ''
        }
        };
    },
    methods: {
        kirimPesan() {
        // Handle form submission
        console.log('Form submitted:', this.form);
        }
    }
});
</script> -->

<template>
    <q-page>

      <!-- Header Section -->
      <div style="padding: 80px 48px 64px; border-bottom: 1px solid #EBEBEB;">
        <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; letter-spacing: 0.12em; color: #6B6B6B; text-transform: uppercase; margin-bottom: 24px;">
          Kontak
        </div>
        <h1 style="font-family: 'Plus Jakarta Sans', sans-serif; font-size: 48px; font-weight: 500; line-height: 1.1; margin: 0 0 24px; max-width: 480px;">
          Mari Kita Ngobrol dan Berkolaborasi
        </h1>
        <p style="font-family: 'Geist Mono', sans-serif; font-size: 16px; line-height: 1.7; color: #6B6B6B; max-width: 480px; margin: 0;">
          Punya project menarik atau sekedar ingin say hi? Aku selalu terbuka untuk diskusi baru.
        </p>
      </div>

      <!-- form Section -->
      <div style="padding: 64px 48px;">
        <div style="display: flex; gap: 80px; flex-wrap: wrap; align-items: flex-start;">

          <!-- form -->
          <div style="flex: 1; min-width: 280px; max-width: 480px;">
            <q-form ref="formRef" @submit="kirimPesan" class="q-gutter-lg">

              <q-input
                v-model="form.nama"
                label="Nama Lengkap"
                :rules="[val => !!val || 'Nama tidak boleh kosong']"
                outlined
                color="dark"
              />

              <q-input
                v-model="form.email"
                label="Email"
                type="email"
                :rules="[
                  val => !!val || 'Email tidak boleh kosong',
                  val => val.includes('@') || 'Email tidak valid'
                ]"
                :outlined
                :color="dark"
              />

              <q-input
                v-model="form.pesan"
                label="Pesan"
                type="textarea"
                rows="5"
                rules="[val => !!val || 'Pesan tidak boleh kosong']"
                :outlined
                color="dark"
              />

              <q-btn
                type="submit"
                label="Kirim Pesan →"
                color="dark"
                unelevated
                style="border-radius: 8px; font-size: 13px; padding: 12px 32px;"
              />

            </q-form>
          </div>

          <!-- Info kontak -->
          <div style="flex-shrink: 0; min-width: 200px;">
            <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; letter-spacing: 0.12rem; color: #6B6B6B; text-transform: uppercase; margin-bottom: 32px;">
              Info Kontak
            </div>

            <div
              v-for="info in kontakInfo"
              :key="info.label"
              style="margin-bottom: 28px;"
            >
              <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; letter-spacing: 0.08em; color: #c9a96e; text-transform: uppercase; margin-bottom: 6px;">
                {{ info.label }}
              </div>
              <div style="font-size: 15px; color: #2D2D2D;">
                {{ info.nilai }}
              </div>
            </div>

          </div>

        </div>
      </div>

    </q-page>
</template>

<script setup>
import { ref } from 'vue'
import {  useQuasar } from 'quasar'

const $q = useQuasar()
const formRef = ref(null)

const form = ref({
    nama: '',
    email: '',
    pesan: ''
})

const kontakInfo =[
  { label: 'Email', nilai: 'andfrz@email.com' },
  { label: 'Lokasi', nilai: 'Indonesia' },
  { label: 'Availability', nilai: 'Open for opportunities' }
]

function kirimPesan(){
    $q.notify({
        type: 'positive',
        message: `Pesan dari ${form.value.nama} berhasil dikirim!`,
        position: 'top'
    })

    // Reset form
    form.value.nama = ''
    form.value.email = ''
    form.value.pesan = ''

    formRef.value.reset()
}
</script>
