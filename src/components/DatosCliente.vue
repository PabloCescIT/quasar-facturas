<template>
  <div>
    <div
      class="text-weight-bold"
    >
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

          <div
            class="items-center q-mb-md"
          >
            <q-btn
              round
              color="primary"
              icon="add"
            />
          </div>

          <div
            class="items-center q-mb-md"
          >
            <q-btn
              flat
              round
              color="primary"
              icon="close"
            />
          </div>
      </div>
  </div>
</template>

<script>
import { ref } from 'vue';

const clienteOptions = [
  'Pablo', 'Carles', 'Alejandro', 'Oscar'
];

export default {
  setup() {
    const options_cliente = ref(clienteOptions);

    const filterFn = (val, update, abort) => {
      if (val.length < 2) {
        abort();
        return;
      }

      update(() => {
        const needle = val.toLowerCase();
        options_cliente.value = clienteOptions.filter(v => v.toLowerCase().indexOf(needle) > -1);
      });
    };

    return {
      buscar_cliente: ref(null),
      options_cliente,
      filterFn,
    };
  },
};
</script>

<style scoped>

</style>
