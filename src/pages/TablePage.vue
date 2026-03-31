<template>
    <q-page>

      <!-- Header Section -->
      <div style="padding: 80px 48px 68px; border-bottom: 1px solid #ebebeb">
        <div style="font-family: 'Geist Mono', sans-serif; font-size: 11px; letter-spacing: 0.12em; color: 6b6b6b; text-transform: uppercase; margin-bottom: 24px;">
          Data
        </div>
        <h1 style="font-family: 'Plus Jakarta Sans', sans-serif; font-size: 48px; font-weight: 500; line-height: 1.1; margin: 0 0 24px;">
          Data Karyawan
        </h1>
        <p style="font-family: 'Geist Mono', sans-serif; font-size: 16px; line-height: 1.7; color: #6B6B6B; max-width: 480px; margin: 0;">
          List seluruh karyawan beserta role dan status aktif mereka.
        </p>
      </div>

      <!-- tabel section -->
      <div style="padding: 48px;">
        <q-table
          :rows="karyawan"
          :columns="columns"
          row-key="id"
          :filter="filter"
          flat
          style="border: 1px solid #ebebeb; border-radius: 12px;"
        >

          <template #top>
            <div style="font-size: 13px; color: #6B6B6B">
              {{ karyawan.length }} karyawan terdaftar
            </div>
            <q-space />
            <q-input
              v-model="filter"
              placeholder="Cari karyawan..."
              dense
              outlined
              color="dark"
              style="min-width: 240px;"
            >
              <template #append>
                <q-icon name="search" size="18px" color="grey" />
              </template>
            </q-input>
          </template>

          <!-- badge aktif/tidak aktif -->
          <template #body-cell-status="props">
            <q-td :props="props">
              <div
                :style="{
                  display: 'inline-block',
                  padding: '4px 12px',
                  borderRadius: '100px',
                  fontSize: '12px',
                  fontWeight: '500',
                  background: 'props.row.status' === 'aktif' ? '#f0fff4' : 'fff5f5',
                  color: props.row.status === 'Aktif' ? '#276749' : '#9B2335',
                  border: `1px solid ${props.row.status === 'Aktif' ? '#C6F6D5' : '#FED7D7'}`
                }"
              >
                {{ props.row.status }}
              </div>
            </q-td>
          </template>

          <template #body-cell-aksi="props">
            <q-td :props="props">
              <q-btn
                flat
                round
                icon="arrow_forward"
                size="12px"
                color="dark"
                @click="lihatDetail(props.row)"
              />
            </q-td>
          </template>

        </q-table>
      </div>

      <!-- dialog detail -->
      <q-dialog v-model="dialogTerbuka">
        <q-card style="min-width: 400px; border-radius: 16px;">

          <q-card-section style="padding: 32px 32px 24px;">
            <div style="font-size: 11px; letter-spacing: 0.12em; color: #6B6B6B; text-transform: uppercase; margin-bottom: 16px;">
              Detail karyawan
            </div>
            <div style="font-family: 'DM Serif Display', serif; font-size: 28px;">
              {{ karyawanDipilih.nama }}
            </div>
          </q-card-section>

          <q-separator />

          <q-card-section style="padding: 24px 32px;">
            <div
              v-for="item in detailItems"
              :key="item.label"
              style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px;"
            >
              <div style="font-size: 12px; letter-spacing: 0.08em; color: #6B6B6B; text-transform: uppercase;">
                {{ item.label }}
              </div>
              <div style="font-size: 14px; color: #2D2D2D; font-weight: 500;">
                {{ item.nilai }}
              </div>
            </div>
          </q-card-section>

          <q-card-actions style="padding: 16px 32px 32px;">
            <q-space />
            <q-btn
              flat
              label="Tutup"
              color="dark"
              v-close-popup
              style="border-radius: 8px; font-size: 13px;"
            />
          </q-card-actions>

        </q-card>
      </q-dialog>

    </q-page>
</template>

<script setup>
import { biDisplay } from '@quasar/extras/bootstrap-icons'
import { ref, computed} from 'vue'

const filter = ref('')
const dialogTerbuka = ref(false)
const karyawanDipilih = ref({})

const columns = [
    { name: 'id', label: 'ID', field: 'id', sortable: true, style: 'width: 60px' },
    { name: 'nama', label: 'Nama', field: 'nama', sortable: true },
    { name: 'role', label: 'Role', field: 'role', sortable: true },
    { name: 'status', label: 'Status', field: 'status', sortable: true },
    { name: 'aksi', label: '', field: 'aksi', style: 'width: 60px' }
]

const karyawan = [
    { id: 1, nama: 'Andika', role: 'UI/UX Designer', status: 'Aktif' },
    { id: 2, nama: 'Budi', role: 'Frontend Developer', status: 'Aktif' },
    { id: 3, nama: 'Citra', role: 'Backend Developer', status: 'Tidak Aktif' },
    { id: 4, nama: 'Dian', role: 'Project Manager', status: 'Aktif' },
    { id: 5, nama: 'Eka', role: 'QA Engineer', status: 'Tidak Aktif' }
]

const detailItems = computed(() => [
  { label: 'ID', nilai: karyawanDipilih.value.id },
  { label: 'Role', nilai: karyawanDipilih.value.role },
  { label: 'Status', nilai: karyawanDipilih.value.status }
])

function lihatDetail(row) {
    karyawanDipilih.value = row
    dialogTerbuka.value = true
}
</script>
