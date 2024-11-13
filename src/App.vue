<template>
  <div id="app" class="container">
    <h1>Administrador de Citas Médicas</h1>
    <FormularioCita @agregar-cita="agregarCita" />
    <div v-if="citas.length === 0" class="no-citas">
      No hay citas registradas.
    </div>
    <div v-else class="lista-citas">
      <CardCita
        v-for="(cita, index) in citas"
        :key="index"
        :cita="cita"
        @eliminar-cita="eliminarCita(index)"
      />
    </div>
  </div>
</template>

<script>
import FormularioCita from './components/FormularioCita.vue';
import CardCita from './components/CardCita.vue';

export default {
  components: { FormularioCita, CardCita },
  data() {
    return {
      citas: []
    };
  },
  methods: {
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1);
    }
  }
};
</script>

<style>
.container {
  max-width: 700px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
}
.no-citas {
  color: gray;
  margin-top: 20px;
}
</style>
