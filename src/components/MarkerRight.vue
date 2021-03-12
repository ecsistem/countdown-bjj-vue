<template>
  <div class="marker">
    <h1>Lutador 2</h1>
    <div style="border: 10px solid #e83f5b; margin-bottom: 10px"></div>
    <ScoresRight :pontoVantagemRight="pontuacao" />
    <ButtonsRight @pontuarVantagem="pegaValorVantagem" />
  </div>
</template>

<script>
import ScoresRight from "./ScoresRight";
import ButtonsRight from "./ButtonsRight";

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
    ScoresRight,
    ButtonsRight,
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