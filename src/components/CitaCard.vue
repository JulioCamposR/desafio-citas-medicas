<template>
    <div :class="gravedadClase" class="cita-card">
      <h4>{{ paciente }}</h4>
      <p><strong>Fecha:</strong> {{ fecha }}</p>
      <p><strong>Hora:</strong> {{ hora }}</p>
      <p><strong>Motivo:</strong> {{ motivo }}</p>
      <button @click="eliminarCita">Eliminar</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['paciente', 'fecha', 'hora', 'gravedad', 'motivo', 'index'],
    computed: {
      gravedadClase() {
        if (this.gravedad === 'grave') return 'fondo-rojo';
        if (this.gravedad === 'medio') return 'fondo-amarillo';
        return 'fondo-verde';
      },
    },
    methods: {
      eliminarCita() {
        this.$emit('eliminar', this.index); // Emitir evento de eliminación
      },
    },
  };
  </script>
  
  <style scoped>
  .cita-card {
    border-radius: 10px;
    padding: 15px;
    margin: 10px;
  }
  
  .fondo-rojo {
    background-color: #ff4242;
  }
  
  .fondo-amarillo {
    background-color: #fff047;
  }
  
  .fondo-verde {
    background-color: #55ff55;
  }
  
  button {
    margin-top: 10px;
    padding: 5px 10px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  </style>
  