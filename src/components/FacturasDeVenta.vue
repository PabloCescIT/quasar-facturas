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

    return {
      fechaInicio,
      fechaFinal,
      estado,
      options_estado,
      search: ref(''),
      right: ref(false),
    }
  }
}
</script>



