<template>
  <div>
    <h1>Problema de Monty Hall</h1>
    <Gift />
  </div>
</template>

<script>
import Gift from "./components/Gift.vue";

export default {
  name: "App", //ajuda na depuração caso apresenta algum erro(ñ obrigatório);
  components: { Gift },
};
</script>

<style scoped></style>
