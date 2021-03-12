<template>
  <div class="buttons">
    <div class="button-points">
      <button>Pontuar +2</button>
      <button>Pontuar +3</button>
      <button>Pontuar +4</button>
      <button @click="pontuarVantagem(1)" style="background: #49b8aa">
        Vantagem +1
      </button>
      <button style="background: #e83f5b">Punição -1</button>
    </div>
    <div class="button-reset">
      <button>-</button>
      <button>-</button>
      <button>-</button>
      <button>-</button>
      <button>-</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    pontuarVantagem(valor) {
      this.$emit("pontuarVantagem", valor);
    },
  },
};
</script>

<style>
.buttons {
  display: grid;
  grid-template-columns: 1.8fr 0.2fr;
  margin-top: 10px;
}

.buttons .button-points {
  display: grid;
  margin-right: 5px;
}

.buttons .button-points button {
  color: #fff;
  background: #4cd62b;
  padding: 10px;
  margin-bottom: 10px;
  border: none;
  /**/
  font-family: Rajdhani;
  font-size: 20px;
  letter-spacing: 0.165em;
  cursor: pointer;
}

.buttons .button-reset {
  display: grid;
}

.buttons .button-reset button {
  background: none;
  padding: 10px;
  margin-bottom: 10px;
  border: none;
  cursor: pointer;
}
</style>