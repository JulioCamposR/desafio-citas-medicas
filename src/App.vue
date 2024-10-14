<template>
  <div id="app">
    <FormularioCitas @nuevaCita="agregarCita" />
    
    <div v-if="citas.length">
      <div v-for="(cita, index) in citas" :key="index">
        <CitaCard
          :paciente="cita.paciente"
          :fecha="cita.fecha"
          :hora="cita.hora"
          :gravedad="cita.gravedad"
          :motivo="cita.motivo"
          :index="index"
          @eliminar="eliminarCita"
        />
      </div>
    </div>
  </div>
</template>

<script>
import FormularioCitas from './components/FormularioCitas.vue';
import CitaCard from './components/CitaCard.vue';

export default {
  components: {
    FormularioCitas,
    CitaCard,
  },
  data() {
    return {
      citas: [],
    };
  },
  methods: {
    agregarCita(nuevaCita) {
      this.citas.push(nuevaCita);
    },
    eliminarCita(index) {
      this.citas.splice(index, 1); // Eliminar la cita en el índice dado
    },
  },
};
</script>
