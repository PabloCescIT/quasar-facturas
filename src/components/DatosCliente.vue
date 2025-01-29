<template>
  <div>
    <div class="text-weight-bold">
      Datos del cliente
    </div>
    <div style="display: flex; align-items: center; justify-content: space-between;">
      <q-select
        filled
        v-model="buscar_cliente"
        use-input
        hide-selected
        fill-input
        label="Buscar cliente"
        input-debounce="0"
        :options="options_cliente"
        @filter="filterFn"
        style="width: 450px;"
        hint="Escribe para buscar"
      >
        <template v-slot:no-option>
          <q-item>
            <q-item-section class="text-grey">
              No existe este cliente
            </q-item-section>
          </q-item>
        </template>
      </q-select>

      <div class="items-center q-mb-md">
        <q-btn
          round
          color="primary"
          icon="add"
          @click="showAltaNuevoCliente = true"
        />
      </div>

      <div class="items-center q-mb-md">
        <q-btn
          flat
          round
          color="primary"
          icon="close"
        />
      </div>

      <q-dialog v-model="showAltaNuevoCliente">
        <q-card style="width:30vw; max-width: 100%;">
          <q-card-section class="q-py-sm q-px-sm bg-primary" style="display: flex; align-items: center; justify-content: space-between;">
            <div class="text-white text-h6 q-pa-sm">
              Alta nuevo cliente
            </div>
            <div style="display: flex; align-items: center; gap: 10px;">
              <q-btn
                flat
                round
                icon="close"
                color="white"
                v-close-popup
              />
            </div>
          </q-card-section>
          <q-card-section
            class="q-ma-md"
          >
            <AltaNuevoCliente/>
          </q-card-section>
        </q-card>
      </q-dialog>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import AltaNuevoCliente from './AltaNuevoCliente.vue';

export default {

  components: {
    AltaNuevoCliente
  },

  setup() {
    const clienteOptions = ['Pablo', 'Carles', 'Alejandro', 'Oscar'];
    const options_cliente = ref(clienteOptions);
    const buscar_cliente = ref(null);
    const showAltaNuevoCliente = ref(false);

    const filterFn = (val, update, abort) => {
      if (val.length < 2) {
        abort();
        return;
      }
      update(() => {
        const needle = val.toLowerCase();
        options_cliente.value = clienteOptions.filter(v => v.toLowerCase().includes(needle));
      });
    };

    return {
      buscar_cliente,
      options_cliente,
      filterFn,
      showAltaNuevoCliente,
    };
  },
};
</script>
