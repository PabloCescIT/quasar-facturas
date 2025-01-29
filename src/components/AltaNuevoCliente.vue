<template>
  <div class="row justify-between items-center q-mb-md">
    <div class="col-6">
      <q-input
      class="q-mr-lg"
      v-model="texto_codigo_cliente"
      label="Código de cliente"
      />
    </div>
    <div class="col-6">
      <q-input
      v-model="texto_nif"
      label="NIF"
      />
    </div>
  </div>

  <div class="row justify-between items-center q-mb-md">
    <div class="col-12">
      <q-input
      v-model="texto_nombre"
      label="Nombre"
      />
    </div>
  </div>

  <div class="row justify-between items-center q-mb-md">
    <div class="col-12">
      <q-input
      v-model="texto_direccion"
      label="Dirección"
      />
    </div>
  </div>

  <div class="row justify-between items-center q-mb-md">
    <div class="col-6">
      <q-input
      class="q-mr-lg"
      v-model="texto_codigo_postal"
      label="Código postal"
      />
    </div>
    <div class="col-6">
      <q-select
      v-model="select_provincias"
      :options="options_provincias"
      label="Provincia"
      />
    </div>
  </div>

  <div class="row justify-between items-center q-mb-md">
    <div class="col-6">
      <q-select
      class="q-mr-lg"
      v-model="select_poblacion"
      :options="options_poblacion"
      label="Población"
      />
    </div>
    <div class="col-6">
      <q-input
      v-model="texto_pais"
      label="País"
      />
    </div>
  </div>

  <div class="row justify-between items-center q-mb-md">
    <div class="col-6">
      <q-input
      class="q-mr-lg"
      v-model="texto_telefono_fijo"
      label="Teléfono fijo"
      />
    </div>
    <div class="col-6">
      <q-input
      v-model="texto_telefono_movil"
      label="Teléfono móvil"
      />
    </div>
  </div>

  <div class="row justify-between items-center q-mb-md">
    <div class="col-6">
      <q-input
      class="q-mr-lg"
      v-model="texto_email"
      label="E-mail"
      />
    </div>
    <div class="col-6">
      <q-input
      v-model="texto_web"
      label="Web"
      />
    </div>
  </div>

  <div class="row">
    <div class="col-12 text-right">
      <q-btn
        class="q-mt-xl"
        color="primary"
        label="Guardar"
      />
    </div>
  </div>

</template>

<script>
import { ref } from 'vue';


export default {

  components: {

  },

  setup() {


    return {

      select_provincias: ref(null),
      options_provincias: [
        'Álava', 'Albacete', 'Alicante', 'Almería', 'Asturias', 'Ávila', 'Badajoz', 'Baleares', 'Barcelona', 'Bizkaia', 'Burgos', 'Cáceres', 'Cádiz', 'Cantabria', 'Castellón', 'Ceuta', 'Ciudad Real', 'Córdoba', 'Cuenca', 'Girona', 'Granada', 'Guadalajara', 'Gipuzkoa', 'Huelva', 'Huesca', 'Jaén', 'La Coruña', 'La Rioja', 'Las Palmas', 'León', 'Lleida', 'Lugo', 'Madrid', 'Málaga', 'Melilla', 'Murcia', 'Navarra', 'Ourense', 'Palencia', 'Pontevedra', 'Salamanca', 'Santa Cruz de Tenerife', 'Segovia', 'Sevilla', 'Soria', 'Tarragona', 'Teruel', 'Toledo', 'Valencia', 'Valladolid', 'Zamora', 'Zaragoza'
      ],

      select_poblacion: ref(null),
      options_poblacion: [
        'Albacete', 'Alicante', 'Almería', 'Ávila', 'Badajoz', 'Barcelona', 'Bilbao', 'Burgos', 'Cáceres', 'Cádiz', 'Castellón de la Plana', 'Ceuta', 'Ciudad Real', 'Córdoba', 'Cuenca', 'Gerona', 'Granada', 'Guadalajara', 'Huelva', 'Huesca', 'Jaén', 'Las Palmas de Gran Canaria', 'León', 'Lérida', 'Logroño', 'Lugo', 'Madrid', 'Málaga', 'Melilla', 'Murcia', 'Orense', 'Oviedo', 'Palencia', 'Palma de Mallorca', 'Pamplona', 'Pontevedra', 'Salamanca', 'San Sebastián', 'Santa Cruz de Tenerife', 'Santander', 'Segovia', 'Sevilla', 'Soria', 'Tarragona', 'Teruel', 'Toledo', 'Valencia', 'Valladolid', 'Vitoria', 'Zamora', 'Zaragoza'
      ]

    };
  },
};
</script>

