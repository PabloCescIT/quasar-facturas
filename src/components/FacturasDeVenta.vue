<template>
  <q-card
    class="q-my-sm q-mx-sm"
  >
    <q-card-section>
      <div
        class="q-table__container column q-table__card q-table--flat q-table--bordered "
      >
        <div
          class="q-table__top row justify-between items-center"
        >
          <div
            class="q-table__title"
          >
            Facturas de Venta
          </div>
          <div
            class="row justify-between items-center"
          >
            <div
            >
            <q-input
              v-model="fechaInicio"
              style="width: 130px;"
              bg-color= "grey-3"
              dense
              filled
              label="Fecha de inicio"
              type="date"
              class="q-mr-sm"
            />
            </div>
            <div>
            <q-input
              v-model="fechaFinal"
              style="width: 130px;"
              bg-color= "grey-3"
              dense
              filled
              label="Fecha final"
              type="date"
              class="q-mr-sm"
            />
            </div>
            <div>
              <q-select
              label="Estado"
              dense
              filled
              style="width: 100px"
              bg-color= "grey-3"
              v-model="estado"
              :options="options_estado"
              class="q-mr-sm"
              />
            </div>
            <div>
              <q-checkbox
                v-model="right"
                label="Sin fecha"
                class="q-mr-sm"
              />
            </div>
            <div>
              <q-input
                v-model="search"
                filled
                type="search"
                dense
                label="Buscar"
                bg-color= "grey-3"
                class="q-mr-sm"
              >
                <template v-slot:append>
                <q-icon name="search" />
                </template>
              </q-input>
            </div>
            <div>
              <q-btn
              icon="mail"
              label="Enviar facturas"
              color="primary"
              style="font-size: 10px"
              class="q-mr-sm"
              stack
              dense
              flat
              />
            </div>
            <div>
              <q-btn
              icon="description"
              label="Excel"
              color="primary"
              style="font-size: 10px"
              class="q-mr-sm"
              stack
              dense
              flat
              />
            </div>
            <div>
              <q-btn
              icon="add"
              label="Nueva factura"
              color="primary"
              style="font-size: 10px"
              class="q-mr-sm"
              stack
              dense
              flat
              />
            </div>
          </div>
        </div>
        <div
          class="q-table__middle scroll row justify-between items-center"
        >
          <q-table
            :rows="rows_facturasVenta"
            :columns="columns_facturasVenta"
            row-key="name"
          >

          <template v-slot:body-cell-base_imponible="props">
            <q-td :props="props">
              {{ props.value.toLocaleString('es-ES', { style: 'currency', currency: 'EUR' }) }}
            </q-td>
          </template>

          <template v-slot:body-cell-total="props">
            <q-td :props="props">
              {{ props.value.toLocaleString('es-ES', { style: 'currency', currency: 'EUR' }) }}
            </q-td>
          </template>

          <template v-slot:body-cell-fecha_pedido="props">
            <q-td :props="props">
              {{ new Date(props.value).toLocaleString('es-ES', { day: '2-digit', month: '2-digit', year: 'numeric', hour: '2-digit', minute: '2-digit', second: '2-digit' }) }}
            </q-td>
          </template>

          </q-table>

        </div>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {

    const fechaInicio = ref(null);
    const fechaFinal = ref(null);
    const estado = ref(null);

    const options_estado = ref([
      'Borrador',
      'Factura',
      'Pendiente de pago',
      'Cobrada'
    ]);

    const columns_facturasVenta = [

  { name: 'numero_factura', align: 'left', label: 'Número de factura', field: 'numero_factura', sortable: true },
  { name: 'cliente', label: 'Cliente', field: 'cliente', sortable: true },
  { name: 'referencia', label: 'Referencia', field: 'referencia', sortable: true},
  { name: 'fecha_factura', label: 'Fecha factura', field: 'fecha_factura', sortable: true },
  { name: 'base_imponible', label: 'Base imponible', field: 'base_imponible', sortable: true},
  { name: 'total', label: 'Total', field: 'total', sortable: true},
  { name: 'estado', label: 'Estado', field: 'estado', sortable: true}
]

const rows_facturasVenta = [
  {
    numero_factura: '2024/00015',
    cliente: 'Pablo',
    referencia: '',
    fecha_factura: '24-01-2025',
    base_imponible: 220,
    total: 226.2,
    estado: '1 Borrador'
  }
]

const formatValue = (value) => {
    if (typeof value === 'number') {
      return value.toLocaleString('es-ES', { style: 'currency', currency: 'EUR' });
    } else if (!value) {
      return 'N/A';
    }
    return value;
  };


    return {
      fechaInicio,
      fechaFinal,
      estado,
      options_estado,
      search: ref(''),
      right: ref(false),
      columns_facturasVenta,
      rows_facturasVenta,
      formatValue
    }
  }
}
</script>



