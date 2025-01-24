<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="row justify-between items-center">
      <q-toolbar>
        <q-btn flat dense round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title> Pablo Company SL </q-toolbar-title>
        <q-btn flat dense round icon="fullscreen" @click="toggleFullScreen" />
        <q-btn flat dense round icon="account_circle" />
      </q-toolbar>
    </q-header>

    <q-footer elevated class="bg-white text-black">
      <q-tabs class="q-my-md">
        <div>
          <q-avatar size="30px" class="q-mr-sm">
            <img src="/src/assets/nopas-logo.png" alt="Logo" />
          </q-avatar>
          © 2025 Nopas
        </div>
        <q-btn
          class="q-px-none q-mx-md"
          dense
          icon="text_snippet"
          flat
          label="Aviso legal"
          style="font-size: 10px"
        />
        <q-btn
          class="q-px-none"
          dense
          icon="cookie"
          flat
          label="Política de cookies"
          style="font-size: 10px"
        />
      </q-tabs>
    </q-footer>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered class="bg-primary">
      <q-list>
        <q-expansion-item
          default-opened
          icon="storefront"
          label="Compra"
          style="color: white"
          class="q-mb-sm"
        >
          <q-card class="bg-primary">
            <q-btn
              default-opened
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
        <q-expansion-item
          default-opened
          icon="sell"
          label="Venta"
          style="color: white"
          class="q-mb-sm"
        >
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
          default-opened
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
        <q-expansion-item
          default-opened
          icon="business"
          label="Empresa"
          style="color: white"
          class="q-mb-sm"
        >
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
      <FacturasDeVenta />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import { useQuasar } from 'quasar'
import FacturasDeVenta from 'src/components/FacturasDeVenta.vue'

const $q = useQuasar()

const leftDrawerOpen = ref(true)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}

const toggleFullScreen = () => {
  if ($q && $q.fullscreen) {
    if ($q.fullscreen.isActive) {
      $q.fullscreen.exit()
    } else {
      $q.fullscreen.request()
    }
  }
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
