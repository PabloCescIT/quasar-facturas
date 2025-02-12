<template>
  <div>
    <div>
      <q-table
        :rows="rowsTablaEditar"
        :columns="columnsTablaEditar"
        row-key="name"
        flat
        :rows-per-page-options="[0]"
        style="width: 100%"
        no-data-label="Sin datos disponibles"
        class="bg-grey-2"
        hide-pagination
      >
        <template v-slot:body-cell-accionesTablaEditar="props">
          <q-td :props="props">
            <div>
              <q-btn flat round dense size="md" color="black" icon="edit" />
              <q-btn flat round dense size="md" color="black" icon="delete" />
            </div>
          </q-td>
        </template>

        <template v-slot:body-cell-cantidadTablaEditar="props">
          <q-td :props="props">
            {{ props.row.cantidadTablaEditar }}
          </q-td>
        </template>

        <template v-slot:body-cell-precioUnidadTablaEditar="props">
          <q-td :props="props">
            {{ formatValue(props.row.precioUnidadTablaEditar) }}
          </q-td>
        </template>

        <template v-slot:body-cell-descuentoTablaEditar="props">
          <q-td :props="props"> {{ props.row.descuentoTablaEditar }} % </q-td>
        </template>

        <template v-slot:body-cell-ivaTablaEditar="props">
          <q-td :props="props"> {{ props.row.ivaTablaEditar }} % </q-td>
        </template>

        <template v-slot:body-cell-reTablaEditar="props">
          <q-td :props="props"> {{ props.row.reTablaEditar }} % </q-td>
        </template>

        <template v-slot:body-cell-biTablaEditar="props">
          <q-td :props="props">
            {{ formatValue(props.row.biTablaEditar) }}
          </q-td>
        </template>
      </q-table>
    </div>

    <div style="display: flex; justify-content: flex-end">
      <q-btn color="primary" label="Añadir líneas" class="q-mx-md q-mt-md" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const columnsTablaEditar = [
  { name: 'codigoTablaEditar', align: 'left', label: 'Código', field: 'codigoTablaEditar' },
  { name: 'descripcionTablaEditar', align: 'left', label: 'Descripción', field: 'descripcionTablaEditar' },
  { name: 'cantidadTablaEditar', align: 'right', label: 'Cantidad', field: 'cantidadTablaEditar' },
  { name: 'precioUnidadTablaEditar', align: 'right', label: 'Precio/Unidad', field: 'precioUnidadTablaEditar' },
  { name: 'descuentoTablaEditar', align: 'center', label: '% Dto', field: 'descuentoTablaEditar' },
  { name: 'ivaTablaEditar', align: 'center', label: '% IVA', field: 'ivaTablaEditar' },
  { name: 'reTablaEditar', align: 'center', label: '% R.E.', field: 'reTablaEditar' },
  { name: 'biTablaEditar', align: 'right', label: 'B.I.', field: 'biTablaEditar' },
  { name: 'accionesTablaEditar', align: 'right', label: 'Acciones', field: 'accionesTablaEditar' },
]

const rowsTablaEditar = ref([
  {
    codigoTablaEditar: '001',
    descripcionTablaEditar: 'Camiseta',
    cantidadTablaEditar: 1,
    precioUnidadTablaEditar: 10.5,
    descuentoTablaEditar: 5,
    ivaTablaEditar: 21,
    reTablaEditar: 5.2,
    biTablaEditar: 10.5,
    accionesTablaEditar: '',
  },
])

const formatValue = (value) => {
  if (typeof value === 'number') {
    return value.toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })
  }
  return value || 'N/A'
}
</script>
