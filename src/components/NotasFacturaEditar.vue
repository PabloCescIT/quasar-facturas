<template>
  <div class="row justify-between items-center q-py-sm">
    <div class="row q-gutter-x-xl">
      <q-input v-model="notasFactura" label="Notas de factura" dense style="width: 1000px" />
    </div>

    <div class="row q-gutter-x-sm justify-end">
      <q-btn color="primary" label="Guardar notas" />
      <q-btn flat round icon="close" color="black" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const notasFactura = ref('')
</script>

