<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />
        <q-toolbar-title> Pablo Company SL </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered class="bg-primary">
      <q-list>
        <q-expansion-item icon="storefront" label="Compra" style="color: white" class="q-mb-sm">
          <q-card class="bg-primary">
            <q-btn
              align="left"
              icon="email"
              label="Proveedores"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
            <q-btn
              align="left"
              icon="shopping_cart"
              label="Facturas de compra"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
          </q-card>
        </q-expansion-item>
        <q-expansion-item icon="sell" label="Venta" style="color: white" class="q-mb-sm">
          <q-card class="bg-primary">
            <q-btn
              align="left"
              icon="contact_page"
              label="Clientes"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
            <q-btn
              align="left"
              icon="request_quote"
              label="Presupuestos"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
            <q-btn
              align="left"
              icon="notes"
              label="Albaranes"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
            <q-btn
              align="left"
              icon="description"
              label="Facturas de Venta"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
          </q-card>
        </q-expansion-item>
        <q-expansion-item
          icon="query_stats"
          label="Estadísticas"
          style="color: white"
          class="q-mb-sm"
        >
          <q-card class="bg-primary">
            <q-btn
              align="left"
              icon="assessment"
              label="Gráficas de compra"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
            <q-btn
              align="left"
              icon="assessment"
              label="Gráficas de venta"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
          </q-card>
        </q-expansion-item>
        <q-expansion-item icon="business" label="Empresa" style="color: white" class="q-mb-sm">
          <q-card class="bg-primary">
            <q-btn
              align="left"
              icon="settings"
              label="Perfil"
              flat
              class="custom-btn q-pl-xl q-py-sm full-width"
            />
          </q-card>
        </q-expansion-item>
        <q-btn
          align="left"
          icon="logout"
          label="Cerrar sesión"
          flat
          class="custom-btn full-width"
          color="white"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>

<style>
/* Los label de los botones por defecto están en mayúsculas y en negrita. Esto lo corrige y los deja normal */
.custom-btn {
  text-transform: none;
  font-weight: normal;
  justify-content: flex-start;
}
</style>
