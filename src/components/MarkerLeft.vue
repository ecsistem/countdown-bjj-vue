<template>
  <div class="marker">
    <h1>Lutador 1</h1>
    <div style="border: 10px solid #5965e0; margin-bottom: 10px"></div>

    <ScoresLeft :pontoVantagemLeft="pontuacao" />
    <ButtonsLeft @pontuarVantagem="pegaValorVantagem" />
  </div>
</template>

<script>
import ScoresLeft from "./ScoresLeft";
import ButtonsLeft from "./ButtonsLeft";

export default {
  methods: {
    pegaValorVantagem(valor) {
      this.pontuacao = this.pontuacao + valor;
    },
  },
  data() {
    return {
      pontuacao: 0,
    };
  },
  components: {
    ScoresLeft,
    ButtonsLeft,
  },
};
</script>

<style>
.marker {
  display: block;
  width: 100%;
  margin: 30px;
  text-align: center;
}
</style>