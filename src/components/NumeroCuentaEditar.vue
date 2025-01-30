<template>
  <div
    class="row justify-between items-center q-py-sm"
    style="display: flex; align-items: center; justify-content: space-between"
  >
    <div class="q-gutter-x-xl">
      <q-select
        filled
        v-model="modelNumeroCuenta"
        use-input
        hide-selected
        fill-input
        input-debounce="0"
        :options="optionsNumeroCuenta"
        @filter="filterFnNumeroCuenta"
        hint="Selecciona el nº de cuenta"
        style="width: 900px; padding-bottom: 32px"
      >
        <template v-slot:no-option>
          <q-item>
            <q-item-section class="text-grey"> No se encuentra la factura </q-item-section>
          </q-item>
        </template>
      </q-select>
    </div>

    <div class="items-center q-gutter-x-sm justify-end" style="margin-bottom: 30px">
      <q-btn round icon="add" color="primary" class="q-mr-sm" />
      <q-btn color="primary" label="Sin nº de cuenta" />
      <q-btn flat round icon="close" color="black" />
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const numeroCuentaOptions = ['123', '456', '789', '000']
    const optionsNumeroCuenta = ref(numeroCuentaOptions)

    const filterFnNumeroCuenta = (val, update, abort) => {
      if (val.length < 2) {
        abort()
        return
      }
      update(() => {
        const needle = val.toLowerCase()
        optionsNumeroCuenta.value = numeroCuentaOptions.filter((v) =>
          v.toLowerCase().includes(needle),
        )
      })
    }

    return {
      optionsNumeroCuenta,
      filterFnNumeroCuenta,
      numeroCuentaOptions,
    }
  },
}
</script>
