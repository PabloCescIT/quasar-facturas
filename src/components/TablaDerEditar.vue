<template>
  <div class="q-mb-lg row justify-end q-mr-md">
    <q-btn flat round dense size="md" color="black" icon="save" />
    <q-btn flat round dense size="md" color="black" icon="close" />
  </div>

  <div class="row justify-between items-center q-mb-md q-ml-md q-mr-sm">
    <div class="col-6 text-weight-bold">Base imponible</div>
    <div class="col-3 row justify-center"></div>
    <div class="col-2">0,01 €</div>
  </div>

  <div class="row justify-between items-center q-mb-md q-ml-md q-mr-sm">
    <div class="col-6 text-weight-bold">Descuento</div>
    <div class="col-3 row justify-center">
      <div>
        <q-input
          v-model.number="model_descuento"
          type="number"
          dense
          filled
          style="width: 70px"
          borderless
          bg-color="grey-2"
          class="no-border-input"
          suffix="%"
        />
      </div>
    </div>
    <div class="col-2">0,00 €</div>
  </div>

  <div class="row justify-between items-center q-mb-md q-ml-md q-mr-sm">
    <div class="col-6 text-weight-bold">Base imponible total</div>
    <div class="col-3 row justify-center"></div>
    <div class="col-2">0,01 €</div>
  </div>

  <div class="row justify-between items-center q-mb-md q-ml-md q-mr-sm">
    <div class="col-6 text-weight-bold">IVA</div>
    <div class="col-3 row justify-center"></div>
    <div class="col-2">0,00 €</div>
  </div>

  <div class="row justify-between items-center q-mb-md q-ml-md q-mr-sm">
    <div class="col-6 text-weight-bold">R.E.</div>
    <div class="col-3 row justify-center"></div>
    <div class="col-2">0,00 €</div>
  </div>

  <div class="row justify-between items-center q-mb-md q-ml-md q-mr-sm">
    <div class="col-6 text-weight-bold">IRPF</div>
    <div class="col-3 row justify-center">
      <div>
        <q-input
          v-model.number="model_irpf"
          type="number"
          dense
          filled
          style="width: 70px"
          borderless
          bg-color="grey-2"
          class="no-border-input"
          suffix="%"
        />
      </div>
    </div>
    <div class="col-2">0,00 €</div>
  </div>

  <div class="row justify-between bg-grey-6 q-pa-sm rounded-borders q-pl-md">
    <div class="col-6 text-weight-bold">Total</div>
    <div class="col-3 row justify-center"></div>
    <div class="col-2 text-weight-bold">0,01 €</div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const model_descuento = ref(0)
const model_irpf = ref(0)
</script>

<style scoped>
.no-border-input :deep(.q-field__control) {
  border-bottom: 1px solid rgb(196, 196, 196) !important;
}
</style>
