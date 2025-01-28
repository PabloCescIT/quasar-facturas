<template>
  <q-card class="q-my-sm q-mx-sm">
    <q-card-section>
      <div class="q-table__container column q-table__card q-table--flat q-table--bordered">
        <div class="q-table__top row justify-between items-center">
          <div class="q-table__title">Facturas de Venta</div>
          <div class="row justify-between items-center">
            <div>
              <q-input
                v-model="fechaInicio"
                style="width: 130px"
                bg-color="grey-3"
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
                style="width: 130px"
                bg-color="grey-3"
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
                bg-color="grey-3"
                v-model="estado"
                :options="options_estado"
                class="q-mr-sm"
              />
            </div>
            <div>
              <q-checkbox v-model="right" label="Sin fecha" class="q-mr-sm" />
            </div>
            <div>
              <q-input
                v-model="search"
                filled
                type="search"
                dense
                label="Buscar"
                bg-color="grey-3"
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
                @click="showNuevaFactura = true"
              />
            </div>
          </div>
        </div>
        <div class="q-table__middle scroll row justify-between items-center">
          <q-table
            :rows="rows_facturasVenta"
            :columns="columns_facturasVenta"
            row-key="name"
            flat
            :rows-per-page-options="[0]"
            style="width: 100%"
            no-data-label="Sin datos disponibles"
          >
            <template v-slot:body-cell-estado="props">
              <q-td :props="props">
                <div>
                  <q-badge class="q-px-md q-py-sm text-black" color="grey-6" :label="props.value" />
                </div>
              </q-td>
            </template>

            <template v-slot:body-cell-acciones_factura="props">
              <q-td :props="props">
                <div>
                  <q-btn flat round dense size="md" color="grey-6" icon="delete" />
                  <q-btn flat round dense size="md" color="grey-6" icon="email" />
                  <q-btn flat round dense size="md" color="grey-6" icon="wysiwyg" />
                </div>
              </q-td>
            </template>

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
                {{
                  new Date(props.value).toLocaleString('es-ES', {
                    day: '2-digit',
                    month: '2-digit',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit',
                    second: '2-digit',
                  })
                }}
              </q-td>
            </template>

            <template v-slot:bottom-row>
              <q-tr class="text-weight-bold">
                <q-td colspan="4" class="text-left">TOTALES:</q-td>
                <q-td class="text-right">
                  {{
                    totales.base_imponible.toLocaleString('es-ES', {
                      style: 'currency',
                      currency: 'EUR',
                    })
                  }}
                </q-td>
                <q-td class="text-right">
                  {{
                    totales.total.toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })
                  }}
                </q-td>
                <q-td></q-td>
              </q-tr>
            </template>
          </q-table>

          <q-dialog
            v-model="showNuevaFactura"
          >
            <q-card
              style="width:68vw; max-width: 100%; "
            >
            <q-card-section
              class="q-py-sm q-px-sm bg-primary"
              style="display: flex; align-items: center; justify-content: space-between;"
            >

              <div class="text-white text-h6 q-pa-sm">
                Factura de Venta:
              </div>

              <div style="display: flex; align-items: center; gap: 10px;">

                <div class="text-weight-bold text-white">
                  Estado factura:
                </div>

                <q-select
                  filled
                  dense
                  v-model="model"
                  :options="options_estado"
                  label="Estado"
                  style="width: 120px;"
                  class="bg-grey-5"
                />

                <q-btn
                  flat
                  round
                  icon="close"
                  color="white"
                  v-close-popup
                />
              </div>
            </q-card-section>
              <q-separator />
              <q-card-section
                class="q-pa-sm q-ma-md bg-grey-2 row"
              >
                <div
                  class="col-6"
                >
                  <q-card-section
                    class="bg-grey-4 q-mr-sm"
                    flat
                  >
                  <DatosEmpresa/>
                  </q-card-section>
                </div>
                <div
                  class="col-6"
                >
                  <q-card-section
                    class="bg-grey-3"
                    flat
                  >
                  <DatosCliente/>
                  </q-card-section>
                </div>
              </q-card-section>
            </q-card>
          </q-dialog>
        </div>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
import { ref, computed } from 'vue'
import DatosEmpresa from './DatosEmpresa.vue'
import DatosCliente from './DatosCliente.vue';


export default {

  components: {
    DatosEmpresa,
    DatosCliente
  },

  setup() {
    const fechaInicio = ref(null)
    const fechaFinal = ref(null)
    const estado = ref(null)
    const showNuevaFactura = ref(false)

    const options_estado = ref(['Borrador', 'Factura', 'Pendiente de pago', 'Cobrada'])

    const columns_facturasVenta = [
      {
        name: 'numero_factura',
        align: 'left',
        label: 'Número de factura',
        field: 'numero_factura',
        sortable: true,
      },
      { name: 'cliente', label: 'Cliente', field: 'cliente', sortable: true },
      { name: 'referencia', label: 'Referencia', field: 'referencia', sortable: true },
      { name: 'fecha_factura', label: 'Fecha factura', field: 'fecha_factura', sortable: true },
      { name: 'base_imponible', label: 'Base imponible', field: 'base_imponible', sortable: true },
      { name: 'total', label: 'Total', field: 'total', sortable: true },
      { name: 'estado', label: 'Estado', field: 'estado', sortable: true },
      { name: 'acciones_factura', label: 'Acciones', field: 'acciones', sortable: true },
    ]

    const rows_facturasVenta = ref([
      {
        numero_factura: '2024/00015',
        cliente: 'Pablo',
        referencia: '',
        fecha_factura: '24-01-2025',
        base_imponible: 220,
        total: 226.2,
        estado: '1 Borrador',
        acciones: '',
      },
    ])

    const formatValue = (value) => {
      if (typeof value === 'number') {
        return value.toLocaleString('es-ES', { style: 'currency', currency: 'EUR' })
      } else if (!value) {
        return 'N/A'
      }
      return value
    }

    const totales = computed(() => {
      let base_imponible = 0
      let total = 0
      rows_facturasVenta.value.forEach((row) => {
        base_imponible += row.base_imponible || 0
        total += row.total || 0
      })
      return { base_imponible, total }
    })

    return {
      fechaInicio,
      fechaFinal,
      estado,
      options_estado,
      search: ref(''),
      right: ref(false),
      columns_facturasVenta,
      rows_facturasVenta,
      formatValue,
      totales,
      showNuevaFactura,
    }
  },
}
</script>
