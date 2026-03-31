<template>
  <q-layout view="lHh Lpr lFf">

    <!-- Header/navbar -->
    <q-header class="bg-white text-dark" style="border-bottom: 1px solid #ebebeb;">
      <q-toolbar style="height: 64px; padding:0 24px;">
        <q-btn
          flat
          round
          icon="menu"
          color="dark"
          @click="toggleSidebar"
        />

        <q-toolbar-title style="font-family: 'Plus Jakarta Sans', sans-serif; font-size: 20px;">
          Portofolio Andika
        </q-toolbar-title>
        <q-btn flat label="Home" color="dark" to="/" style="font-size: 13px;" />

      </q-toolbar>
    </q-header>

    <!-- Sidebar -->
    <q-drawer v-model="sidebarTerbuka" show-if-above bordered style="background: #F8F7F4;">
      <div style="padding: 32px 16px 16px;">
        <div style="font-family: 'Geist Mono', sans-serif; font-size: 22px; margin-bottom: 4px;">
          Andika
        </div>
        <div style="font-size: 13px; color: #6b6b6b;">
          Test Sub Text - andika
        </div>
      </div>

      <q-separator style="margin: 0 16px;" />
      <q-list style="padding: 16px 8px;">

        <q-item
          clickable
          to="/"
          exact
          active-class="sidebar-active"
          style="border-radius: 8px; margin-bottom: 4px;"
        >
          <q-item-section avatar>
            <q-icon name="home" size="20px" />
          </q-item-section>
          <q-item-section style="font-size: 14px;">Home</q-item-section>
        </q-item>

        <q-item
          clickable
          to="/about"
          active-class="sidebar-active"
          style="border-radius: 8px; margin-bottom: 4px;"
        >
          <q-item-section avatar>
            <q-icon name="person" size="20px" />
          </q-item-section>
          <q-item-section style="font-size: 14px;">About</q-item-section>
        </q-item>

        <q-item
          clickable
          to="/contact"
          active-class="sidebar-active"
          style="border-radius: 8px; margin-bottom: 4px;"
        >
          <q-item-section avatar>
            <q-icon name="mail" size="20px" />
          </q-item-section>
          <q-item-section style="font-size: 14px;">Contact</q-item-section>
        </q-item>

        <q-item
          clickable
          to="/table"
          active-class="sidebar-active"
          style="border-radius: 8px; margin-bottom: 4px;"
        >
          <q-item-section avatar>
            <q-icon name="table_chart" size="20px" />
          </q-item-section>
          <q-item-section style="font-size: 14px;">Data Karyawan</q-item-section>
        </q-item>

        <q-item
          clickable
          to="/stepper"
          active-class="sidebar-active"
          style="border-radius: 8px; margin-bottom: 4px;"
        >
          <q-item-section avatar>
            <q-icon name="assignment" size="20px" />
          </q-item-section>
          <q-item-section style="font-size: 14px;">Registrasi</q-item-section>
        </q-item>

      </q-list>
    </q-drawer>

    <!-- konten halaman -->
    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script setup>
import { ref } from 'vue'

const sidebarTerbuka = ref(false)

function toggleSidebar() {
  sidebarTerbuka.value = !sidebarTerbuka.value
}
</script>

<style>
.sidebar-active {
  background-color: #2d2d2d !important;
  color: white !important;
}

.sidebar-active q-icon {
  color: white !important;
}
</style>
