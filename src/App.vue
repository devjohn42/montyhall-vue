<template>
  <h1>Problema de Monty Hall</h1>
  <div class="form">
    <div v-if="!started">
      <label for="doorsAmount">Quantas Portas ?</label>
      <input
        type="text"
        id="doorsAmount"
        size="3"
        v-model.number="doorsAmount"
      />
    </div>
    <div v-if="!started">
      <label for="selectedDoor">Qual a porta premiada ?</label>
      <input
        type="text"
        id="selectedDoor"
        size="3"
        v-model.number="selectedDoor"
      />
    </div>
    <button v-if="!started" @click="started = true">Iniciar</button>
    <button v-if="started" @click="started = false">Reiniciar</button>
  </div>
  <div class="doors" v-if="started">
    <div v-for="i in doorsAmount" :key="i">
      <Door :has-gift="i === selectedDoor" :number="i" />
    </div>
  </div>
</template>

<script>
import Door from "./components/Door.vue";

export default {
  name: "App", //ajuda na depuração caso apresenta algum erro(ñ obrigatório);
  components: { Door },
  data: () => {
    return {
      started: false,
      doorsAmount: 3,
      selectedDoor: null,
    };
  },
};
</script>

<style>
.form {
  display: flex;
  flex-direction: column;
  gap: 8px;
  align-items: center;
  justify-content: center;

  margin-bottom: 40px;

  font-size: 1.3rem;
}

.form label {
  font-weight: bold;
}

.form input {
  background-color: #0005;
  padding: 5px;
  margin-left: 8px;

  color: white;
  font-size: 1rem;
  font-weight: bold;

  border: 2px solid #2aa55d;
  border-radius: 8px;
  outline: none;
}

.form button {
  background-color: #0005;
  padding: 5px 20px;
  margin-top: 40px;

  color: white;
  font-size: 1.3rem;
  font-weight: bold;

  border: 2px solid #2aa55d;
  border-radius: 8px;
  outline: none;

  transition: 0.3s;
}

.form button:hover {
  background-color: #0008;
  border: 2px solid #13e269;
  transition: 0.4s;
  cursor: pointer;
}

.doors {
  display: flex;
  align-self: stretch;
  justify-content: space-around;

  flex-wrap: wrap;
}
</style>
