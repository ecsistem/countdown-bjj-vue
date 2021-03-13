<template>
  <div class="marker">
    <h1>Lutador 2</h1>
    <div style="border: 10px solid #e83f5b; margin-bottom: 10px"></div>
    <ScoresRight
      :pontoVantagemRight="pontuacaoVantagem"
      :quantidadePunicao="pontuacaoPunicao"
      :pontos="pontuacao"
    />
    <ButtonsRight
      @pontuarVantagem="pegaValorVantagem"
      @pontuarPunicao="pegaValorPunicao"
      @pontuar="pegaValorPontos"
      @reverter="pegaValorReverter"
    />
  </div>
</template>

<script>
import ScoresRight from "./ScoresRight";
import ButtonsRight from "./ButtonsRight";

export default {
  methods: {
    pegaValorReverter(valor) {
      if ((valor === 4 || valor === 3 || valor === 2) && this.pontuacao > 0) {
        this.pontuacao = this.pontuacao - valor;
      }
      if (valor === 1 && this.pontuacaoVantagem > 0) {
        this.pontuacaoVantagem = this.pontuacaoVantagem - valor;
      }
      if (valor === -1 && this.pontuacaoPunicao < 0) {
        this.pontuacaoPunicao = this.pontuacaoPunicao - valor;
      }
    },
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