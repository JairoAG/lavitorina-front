<template>
  <div class="container">
    <header>
      <h1>LA VITORINA</h1>
    </header>
    <div class="form-container">
      <p>{{ currentDateTime }}</p>
      <div>
        <label for="children">Niños:</label>
        <input v-model="childrenCount" id="children" type="number" />
      </div>
      <div>
        <label for="adults">Adultos:</label>
        <input v-model="adultsCount" id="adults" type="number" />
      </div>
      <div>
        <label for="time">Hora:</label>
        <input v-model="currentTime" id="time" type="text" readonly />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentDateTime: '',
      currentTime: '',
      childrenCount: 0,
      adultsCount: 0,
    };
  },
  created() {
    this.updateDateTime();
    setInterval(this.updateDateTime, 1000); // Actualizar cada segundo
  },
  methods: {
    updateDateTime() {
      const now = new Date();
      this.currentDateTime = now.toLocaleString();
      this.currentTime = now.toLocaleTimeString();
    },
  },
};
</script>

<style scoped>
.container {
  background-color: #333; /* Gris oscuro */
  color: white;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

header {
  text-align: center;
  width: 100%;
  position: absolute;
  top: 20px;
}

h1 {
  font-size: 2.5rem;
  margin: 0;
}

.form-container {
  text-align: center;
}

label {
  display: block;
  margin-top: 10px;
}

input {
  margin-bottom: 10px;
}
</style>
