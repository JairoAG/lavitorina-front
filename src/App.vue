<template>
  <div class="container">
    <h1>LA VITORINA</h1>
    <div class="form-group">
      <label for="currentDateTime">Fecha y Hora Actual:</label>
      <input type="text" id="currentDateTime" v-model="currentDateTime" readonly />
    </div>
    <div class="form-group">
      <label for="children">Niños:</label>
      <input type="number" id="children" v-model="children" min="0" />
    </div>
    <div class="form-group">
      <label for="adults">Adultos:</label>
      <input type="number" id="adults" v-model="adults" min="0" />
    </div>
    <div class="form-group">
      <label for="tramName">Nombre del Tranvía:</label>
      <select id="tramName" v-model="tramName">
        <option>Tranvía Chico</option>
        <option>Tranvía Grande</option>
        <option>Tranvía Doble</option>
        <option>Safari</option>
        <option>Raizer</option>
        <option>Camioneta</option>
      </select>
    </div>
    <div class="form-group">
      <label for="tourType">Tipo de Recorrido:</label>
      <select id="tourType" v-model="tourType">
        <option>Tradicional</option>
        <option>Mirador</option>
        <option>Jardín Mágico</option>
        <option>Vistas al volcán</option>
      </select>
    </div>
    <div class="form-group">
      <label for="tourTime">Hora del Recorrido:</label>
      <input type="time" id="tourTime" v-model="tourTime" />
    </div>
    <div class="form-group">
      <label for="total">Total a Pagar:</label>
      <div class="currency-input">
        <span class="currency-symbol">$</span>
        <input type="number" id="total" v-model="total" min="0" />
      </div>
    </div>
    <div class="buttons">
      <button @click="register">Registrar</button>
      <button @click="clearForm">Limpiar</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentDateTime: '',
      children: 0,
      adults: 0,
      tramName: '',
      tourType: '',
      tourTime: '',
      total: 0,
    };
  },
  created() {
    this.updateDateTime();
    setInterval(this.updateDateTime, 1000);
  },
  methods: {
    updateDateTime() {
      const now = new Date();
      const day = String(now.getDate()).padStart(2, '0');
      const month = String(now.getMonth() + 1).padStart(2, '0');
      const year = now.getFullYear();
      const hours = String(now.getHours()).padStart(2, '0');
      const minutes = String(now.getMinutes()).padStart(2, '0');
      const seconds = String(now.getSeconds()).padStart(2, '0');
      this.currentDateTime = `${day}/${month}/${year} ${hours}:${minutes}:${seconds}`;
    },
    register() {
      if (!this.children || !this.adults || !this.tourTime || !this.tramName || !this.tourType || !this.total) {
        alert('Todos los campos deben ser llenados.');
        return;
      }
      // Aquí puedes añadir la lógica para registrar los datos
      alert('Datos registrados exitosamente.');
    },
    clearForm() {
      this.children = 0;
      this.adults = 0;
      this.tramName = '';
      this.tourType = '';
      this.tourTime = '';
      this.total = 0;
    },
  },
};
</script>

<style>
.container {
  background-color: #2f2f2f;
  color: white;
  padding: 20px;
  border-radius: 8px;
  width: 300px;
  margin: 0 auto;
  text-align: left;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input, select {
  width: 100%;
  padding: 8px;
  border-radius: 4px;
  border: 1px solid #ccc;
}

input[type="text"] {
  background-color: #444;
  color: white;
  border: none;
}

input[type="number"] {
  background-color: #fff;
  color: #000;
}

input[type="number"]::placeholder {
  color: #999;
}

.currency-input {
  display: flex;
  align-items: center;
}

.currency-symbol {
  margin-right: 8px;
  color: #000;
}

.buttons {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  background-color: #4CAF50;
  color: white;
  font-weight: bold;
}

button:nth-child(2) {
  background-color: #f44336;
}
</style>
