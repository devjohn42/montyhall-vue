<template>
  <h1>Problema de Monty Hall</h1>
  <Door :number="1" :has-gift="false" />
</template>

<script>
import Door from "./components/Door.vue";

export default {
  name: "App", //ajuda na depuração caso apresenta algum erro(ñ obrigatório);
  components: { Door },
};
</script>

<style></style>
