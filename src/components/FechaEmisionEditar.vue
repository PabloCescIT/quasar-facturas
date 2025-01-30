<template>
  <div class="row justify-between items-center q-py-sm">
    <div class="row q-gutter-x-xl">
      <q-input
        v-model="fechaEmisionEditar"
        style="width: 200px"
        bg-color="grey-2"
        dense
        label="Fecha emisión"
        type="date"
      />
      <q-input
        v-model="fechaVencimientoEditar"
        style="width: 200px"
        bg-color="grey-2"
        dense
        label="Fecha de vencimiento"
        type="date"
      />
      <q-input v-model="text_referencia" label="Referencia" dense style="width: 400px" />
    </div>

    <div class="row q-gutter-x-sm justify-end">
      <q-btn color="primary" label="Guardar" />
      <q-btn flat round icon="close" color="black" />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const fechaEmisionEditar = ref(null)
    const fechaVencimientoEditar = ref(null)

    return {
      fechaEmisionEditar,
      fechaVencimientoEditar,
      text_referencia: ref(''),
    }
  },
}
</script>
