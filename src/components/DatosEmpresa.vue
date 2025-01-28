<template>
  <div class="text-weight-bold">
    Datos de la empresa
  </div>
  <div>
    <q-table
      flat
      :rows="rows"
      :columns="columns"
      row-key="name"
      hide-header
      hide-bottom
      style="width: 100%"
      class="bg-grey-4 no-separator"
    />
  </div>
</template>

<script>
const columns = [
  { name: 'datos_1', align: 'left', field: 'datos_1', style: 'padding-left: 0;' },
  { name: 'datos_2', align: 'left', field: 'datos_2' },
  { name: 'datos_3', align: 'left', field: 'datos_3' },
]

const rows = [
  {
    datos_1: 'Pablo SL',
    datos_2: '',
    datos_3: '39419918B',
  },
  {
    datos_1: 'Carrer Josep Pla',
    datos_2: '',
    datos_3: '',
  },
  {
    datos_1: 'Mataró',
    datos_2: '',
    datos_3: '08304',
  },
]

export default {
  setup() {
    return {
      columns,
      rows,
    }
  },
}
</script>

<style scoped>
.no-separator .q-table__middle .q-table__grid-content .q-table__row {
  border-bottom: none;
}
</style>
