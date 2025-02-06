<template>
  <div>
    <div>
      <q-table
        :rows="rowsTablaIzqEditar"
        :columns="columnsTablaIzqEditar"
        row-key="name"
        flat
        dense
        :rows-per-page-options="[0]"
        style="width: 100%"
        no-data-label="Sin datos disponibles"
        class="bg-grey-2"
        hide-pagination
      >

        <template v-slot:body-cell-ivaMonetarioIzq="props">
          <q-td :props="props">
            {{ formatValue(props.row.ivaMonetarioIzq) }}
          </q-td>
        </template>

        <template v-slot:body-cell-baseImponibleIzqEditar="props">
          <q-td :props="props">
            {{ formatValue(props.row.baseImponibleIzqEditar) }}
          </q-td>
        </template>

        <template v-slot:body-cell-ivaPorcentajeIzq="props">
          <q-td :props="props"> {{ props.row.ivaPorcentajeIzq }} % </q-td>
        </template>

      </q-table>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const columnsTablaIzqEditar = [

      {
        name: 'baseImponibleIzqEditar',
        align: 'left',
        label: 'B.I.',
        field: 'baseImponibleIzqEditar',
      },
      {
        name: 'ivaPorcentajeIzq',
        align: 'right',
        label: '% IVA',
        field: 'ivaPorcentajeIzq',
      },
      {
        name: 'ivaMonetarioIzq',
        align: 'right',
        label: '€ IVA',
        field: 'ivaMonetarioIzq',
      }

    ]

    const rowsTablaIzqEditar = ref([
      {
        baseImponibleIzqEditar: 0.01,
        ivaPorcentajeIzq: 21,
        ivaMonetarioIzq: 0,
      },
    ])

    const formatValue = (value) => {
      if (typeof value === 'number') {
        return value.toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })
      }
      return value || 'N/A'
    }

    return {
      columnsTablaIzqEditar,
      rowsTablaIzqEditar,
      formatValue,
    }
  },
}
</script>
