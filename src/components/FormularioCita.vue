<template>
    <form @submit.prevent="enviarCita" class="formulario">
      <!-- Campo de Paciente -->
      <div class="campo">
        <label :style="{ color: !paciente ? 'red' : 'black' }">Paciente</label>
        <input 
          type="text" 
          v-model="paciente" 
          @input="validarFormulario" 
          placeholder="Ingrese nombre del paciente" 
        />
      </div>
  
      <!-- Campo de Fecha -->
      <div class="campo">
        <label :style="{ color: !fecha ? 'red' : 'black' }">Fecha</label>
        <input 
          type="date" 
          v-model="fecha" 
          @input="validarFormulario" 
        />
      </div>
  
      <!-- Campo de Hora -->
      <div class="campo">
        <label :style="{ color: !hora ? 'red' : 'black' }">Hora</label>
        <input 
          type="time" 
          v-model="hora" 
          @input="validarFormulario" 
        />
      </div>
  
      <!-- Campo de Gravedad -->
      <div class="campo">
        <label :style="{ color: !gravedad ? 'red' : 'black' }">Gravedad</label>
        <select v-model="gravedad" @change="validarFormulario">
          <option value="">Seleccione</option>
          <option value="Baja">Baja</option>
          <option value="Media">Media</option>
          <option value="Alta">Alta</option>
        </select>
      </div>
  
      <!-- Campo de Motivo -->
      <div class="campo">
        <label :style="{ color: !motivo ? 'red' : 'black' }">Motivo</label>
        <input 
          type="text" 
          v-model="motivo" 
          @input="validarFormulario" 
          placeholder="Ingrese motivo de la consulta" 
        />
      </div>
  
      <!-- Botón de Agregar -->
      <button :disabled="!formularioValido">Agregar</button>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        paciente: '',
        fecha: '',
        hora: '',
        gravedad: '',
        motivo: '',
        formularioValido: false
      };
    },
    methods: {
      validarFormulario() {
        // Verificar que todos los campos tengan valor
        this.formularioValido = this.paciente && this.fecha && this.hora && this.gravedad && this.motivo;
      },
      enviarCita() {
        const nuevaCita = {
          paciente: this.paciente,
          fecha: this.fecha,
          hora: this.hora,
          motivo: this.motivo,
          gravedad: this.gravedad
        };
        this.$emit('agregar-cita', nuevaCita);
        this.resetFormulario();
      },
      resetFormulario() {
        this.paciente = '';
        this.fecha = '';
        this.hora = '';
        this.gravedad = '';
        this.motivo = '';
        this.formularioValido = false;
      }
    }
  };
  </script>
  
  <style>
  .formulario {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
    margin-top: 20px;
  }
  .campo {
    flex: 1;
    display: flex;
    flex-direction: column;
  }
  button:disabled {
    background-color: gray;
    cursor: not-allowed;
  }
  </style>
  