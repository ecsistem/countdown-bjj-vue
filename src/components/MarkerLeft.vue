<template>
  <div class="marker">
    <h1>Lutador 1</h1>
    <div style="border: 10px solid #5965e0; margin-bottom: 10px"></div>

    <ScoresLeft
      :pontoVantagemLeft="pontuacaoVantagem"
      :quantidadePunicao="pontuacaoPunicao"
      :pontos="pontuacao"
    />
    <ButtonsLeft
      @pontuarVantagem="pegaValorVantagem"
      @pontuarPunicao="pegaValorPunicao"
      @pontuar="pegaValorPontos"
    />
  </div>
</template>

<script>
import ScoresLeft from "./ScoresLeft";
import ButtonsLeft from "./ButtonsLeft";

export default {
  methods: {
    pegaValorPontos(valor) {
      this.pontuacao = this.pontuacao + valor;
    },
    pegaValorVantagem(valor) {
      this.pontuacaoVantagem = this.pontuacaoVantagem + valor;
    },
    pegaValorPunicao(valor) {
      this.pontuacaoPunicao = this.pontuacaoPunicao - valor;
    },
  },
  data() {
    return {
      pontuacaoVantagem: 0,
      pontuacaoPunicao: 0,
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