<template>
  <div class="buttons">
    <div class="button-points">
      <button @click="pontuar(2)">Pontuar +2</button>
      <button @click="pontuar(3)">Pontuar +3</button>
      <button @click="pontuar(4)">Pontuar +4</button>
      <button @click="pontuarVantagem(1)" style="background: #49b8aa">
        Vantagem +1
      </button>
      <button @click="pontuarPunicao(1)" style="background: #e83f5b">
        Punição -1
      </button>
    </div>
    <div class="button-reset">
      <button @click="reverter(2)">-</button>
      <button @click="reverter(3)">-</button>
      <button @click="reverter(4)">-</button>
      <button @click="reverter(1)">-</button>
      <button @click="reverter(-1)">-</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    reverter(valor) {
      this.$emit("reverter", valor);
    },
    pontuar(quantidadePontos) {
      this.$emit("pontuar", quantidadePontos);
    },
    pontuarVantagem(valor) {
      this.$emit("pontuarVantagem", valor);
    },
    pontuarPunicao(valor) {
      this.$emit("pontuarPunicao", valor);
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