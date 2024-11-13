<template>
    <div :class="['card', colorGravedad]">
      <h3>{{ cita.paciente }}</h3>
      <p><strong>Fecha:</strong> {{ cita.fecha }}</p>
      <p><strong>Hora:</strong> {{ cita.hora }}</p>
      <p><strong>Motivo:</strong> {{ cita.motivo }}</p>
      <p><strong>Gravedad:</strong> {{ cita.gravedad }}</p>
      <button @click="$emit('eliminar-cita')">Eliminar</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['cita'],
    computed: {
      colorGravedad() {
        switch (this.cita.gravedad) {
          case 'Baja':
            return 'baja';
          case 'Media':
            return 'media';
          case 'Alta':
            return 'alta';
          default:
            return '';
        }
      }
    }
  };
  </script>
  
  <style>
  /* Estilo general para las tarjetas */
  .card {
    border: 1px solid #ccc;
    border-radius: 10px;
    padding: 20px;
    margin: 15px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    text-align: center;
  }
  
  /* Colores para cada nivel de gravedad */
  .baja {
    background-color: #01fa01; /* Verde */
  }
  
  .media {
    background-color: #fafa09; /* Amarillo */
  }
  
  .alta {
    background-color: #ff0606; /* Rojo */
  }
  
  /* Estilo del botón */
  button {
    margin-top: 20px;
    background-color: #333;
    color: white;
    border: none;
    padding: 10px;
    border-radius: 5px;
    cursor: pointer;
    width: 100%;
  }
  
  button:hover {
    background-color: #555;
  }
  
  /* Responsividad */
  .lista-citas {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  </style>
  