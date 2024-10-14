<template>
  <div class="form-container">
    <form @submit.prevent="emitirNuevaCita">
      <div class="form-group">
        <label for="paciente">Paciente</label>
        <input
          v-model="paciente"
          type="text"
          id="paciente"
          placeholder="Nombre del paciente"
        />
      </div>

      <div class="form-group">
        <label for="fecha">Fecha</label>
        <input v-model="fecha" type="date" id="fecha" />
      </div>

      <div class="form-group">
        <label for="hora">Hora</label>
        <input v-model="hora" type="time" id="hora" />
      </div>

      <div class="form-group">
        <label for="gravedad">Gravedad</label>
        <select v-model="gravedad" id="gravedad">
          <option value="grave">Grave</option>
          <option value="medio">Medio</option>
          <option value="bajo">Bajo</option>
        </select>
      </div>

      <div class="form-group">
        <label for="motivo">Motivo</label>
        <input
          v-model="motivo"
          type="text"
          id="motivo"
          placeholder="Motivo de la consulta"
        />
      </div>

      <button type="submit" :disabled="!formularioValido" class="agregar-btn">
        Agregar
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      paciente: '',
      fecha: '',
      hora: '',
      gravedad: 'bajo',
      motivo: '',
    };
  },
  computed: {
    formularioValido() {
      return this.paciente && this.fecha && this.hora && this.motivo;
    },
  },
  methods: {
    emitirNuevaCita() {
      const nuevaCita = {
        paciente: this.paciente,
        fecha: this.fecha,
        hora: this.hora,
        gravedad: this.gravedad,
        motivo: this.motivo,
      };
      this.$emit('nuevaCita', nuevaCita);
      this.resetForm();
    },
    resetForm() {
      this.paciente = '';
      this.fecha = '';
      this.hora = '';
      this.gravedad = 'bajo';
      this.motivo = '';
    },
  },
};
</script>

<style scoped>
.form-container {
  padding: 20px;
  border-radius: 10px;
  width: 80%;
  margin: 0 auto;
}

.form-group {
  display: inline-block;
  margin: 10px;
}

label {
  display: block;
  color: red;
  font-weight: bold;
  margin-bottom: 5px;
}

input, select {
  width: 100%;
  padding: 8px;
  border-radius: 5px;
}

.agregar-btn {
  display: block;
  margin-top: 20px;
  background-color: lightgray;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.agregar-btn:disabled {
  background-color: #ccc;
}
</style>
