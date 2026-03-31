<template>
  <q-page>
    <!-- header section -->
    <div style="padding: 80px 48px 64px; border-bottom: 1px solid #ebebeb">
      <div
        style="
          font-family: 'Geist Mono', sans-serif;
          font-size: 11px;
          letter-spacing: 0.12em;
          color: #6b6b6b;
          text-transform: uppercase;
          margin-bottom: 24px;
        "
      >
        Registrasi
      </div>
      <h1
        style="
          font-family: 'Plus Jakarta Sans', sans-serif;
          font-size: 48px;
          font-weight: 500;
          line-height: 1.1;
          margin: 0 0 24px;
        "
      >
        Form Registrasi
      </h1>
      <p
        style="
          font-family: 'Geist Mono', sans-serif;
          font-size: 16px;
          line-height: 1.7;
          color: #6b6b6b;
          max-width: 480px;
          margin: 0;
        "
      >
        Lengkapi data diri kamu dalam beberapa langkah mudah.
      </p>
    </div>

    <!-- stepper section -->
    <div style="padding: 64px 48px">
      <div style="max-width: 600px">
        <!-- step indicator custom -->
        <div style="display: flex; align-items: center; margin-bottom: 48px">
          <div
            v-for="(label, index) in stepLabels"
            :key="label"
            style="display: flex; align-items: center; flex: 1"
          >
            <div
              style="
                display: flex;
                flex-direction: column;
                align-items: center;
                gap: 8px;
              "
            >
              <div
                :style="{
                  width: '32px',
                  height: '32px',
                  borderRadius: '50%',
                  display: 'flex',
                  alignItems: 'center',
                  justifyContent: 'center',
                  fontSize: '13px',
                  fontWeight: '500',
                  background:
                    step > index + 1
                      ? '#2d2d2d'
                      : step === index + 1
                        ? '#2d2d2d'
                        : 'white',
                  color: step >= index + 1 ? 'white' : '#6b6b6b',
                  border: step >= index + 1 ? 'none' : '1px solid #ebebeb',
                  transition: 'all 0.3s',
                }"
              >
                {{ step > index + 1 ? "✓" : index + 1 }}
              </div>
              <div
                style="
                  font-size: 11px;
                  letter-spacing: 0.06rem;
                  color: #6b6b6b;
                  text-transform: uppercase;
                  white-space: nowrap;
                "
              >
                {{ label }}
              </div>
            </div>
            <div
              v-if="index < stepLabels.length - 1"
              :style="{
                flex: 1,
                height: '1px',
                background: step > index + 1 ? '#2d2d2d' : '#ebebeb',
                margin: '0 8px',
                marginBottom: '28px',
                transition: 'background 0.3s',
              }"
            />
          </div>
        </div>

        <!-- step content -->
        <div
          style="
            background: white;
            border: 1px solid #ebebeb;
            border-radius: 16px;
            padding: 40px;
          "
        >
          <!-- step 1 -->
          <div v-if="step === 1">
            <div
              style="
                font-family: 'Plus Jakarta Sans', sans-serif;
                font-size: 24px;
                margin-bottom: 32px;
              "
            >
              Data Pribadi
            </div>
            <q-input
              v-model="form.nama"
              label="Nama Lengkap"
              outlined
              color="dark"
              class="q-mb-lg"
            />
            <q-input
              v-model="form.email"
              label="Email"
              type="email"
              outlined
              color="dark"
            />
          </div>

          <!-- step 2 -->
          <div v-if="step === 2">
            <div
              style="
                font-family: 'Plus Jakarta Sans', sans-serif;
                font-size: 24px;
                margin-bottom: 32px;
              "
            >
              Data Pekerjaan
            </div>
            <q-input
              v-model="form.perusahaan"
              label="Perusahaan"
              outlined
              color="dark"
              class="q-mb-lg"
            />
            <q-input
              v-model="form.role"
              :options="roleOptions"
              label="Role"
              outlined
              color="dark"
            />
          </div>

          <!-- step 3 -->
          <div v-if="step === 3">
            <div
              style="
                font-family: 'Plus Jakarta Sans', sans-serif;
                font-size: 24px;
                margin-bottom: 32px;
              "
            >
              Konfirmasi Data
            </div>
            <div
              v-for="item in konfirmasiItems"
              :key="item.label"
              style="
                display: flex;
                justify-content: space-between;
                align-items: center;
                padding: 16px 0;
                border-bottom: 1px solid #ebebeb;
              "
            >
              <div
                style="
                  font-size: 12px;
                  letter-spacing: 0.08em;
                  color: #6b6b6b;
                  text-transform: uppercase;
                "
              >
                {{ item.label }}
              </div>
              <div style="font-size: 14px; color: #2d2d2d; font-weight: 500">
                {{ item.nilai }}
              </div>
            </div>
          </div>

          <!-- navigasi -->
          <div
            style="
              display: flex;
              justify-content: space-between;
              margin-top: 40px;
            "
          >
            <q-btn
              v-if="step > 1"
              flat
              label="← Kembali"
              color="dark"
              @click="step--"
              style="border-radius: 8px; font-size: 13px"
            />
            <q-space />
            <q-btn
              v-if="step < 3"
              label="Lanjut →"
              color="dark"
              unelevated
              @click="step++"
              style="border-radius: 8px; font-size: 13px; padding: 10px 28px"
            />
            <q-btn
              v-if="step === 3"
              label="Submit →"
              color="dark"
              unelevated
              @click="submit"
              style="border-radius: 8px; font-size: 13px; padding: 10px 28px"
            />
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref, computed } from "vue";
import { useQuasar } from "quasar";

const $q = useQuasar();
const step = ref(1);

const stepLabels = ["Data Pribadi", "Pekerjaan", "Konfirmasi"];

const form = ref({
  nama: "",
  email: "",
  perusahaan: "",
  role: "",
});

const roleOptions = [
  "UI/UX Designer",
  "Frontend Developer",
  "Backend Developer",
  "Project Manager",
  "QA Engineer",
];

const konfirmasiItems = computed(() => [
  { label: "Nama", nilai: form.value.nama },
  { label: "Email", nilai: form.value.email },
  { label: "Perusahaan", nilai: form.value.perusahaan },
  { label: "Role", nilai: form.value.role },
]);

function submit() {
  $q.notify({
    type: "positive",
    message: `Registrasi ${form.value.nama} berhasil!`,
    position: "top",
  });
  step.value = 1;
  form.value = { nama: "", email: "", perusahaan: "", role: "" };
}
</script>
