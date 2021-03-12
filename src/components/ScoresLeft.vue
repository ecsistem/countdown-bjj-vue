<template>
  <div class="scores">
    <span>{{ quantidadePunicao }}</span>
    <span>{{ pontoVantagemLeft }}</span>
    <span>{{ pontos }}</span>
    <p>P</p>
    <p>V</p>
    <p>PT</p>
  </div>
</template>

<script>
export default {
  props: {
    pontoVantagemLeft: Number,
    quantidadePunicao: Number,
    pontos: Number,
  },
};
</script>

<style>
.scores {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  justify-items: center;
  text-align: center;
  color: #2e384d;
}

.scores span {
  border-radius: 5px;
  padding: 5px;
  font-size: 80px;
  line-height: 70px;
  background: #fff;
}

.scores p {
  font-size: 30px;
  line-height: 38px;
  letter-spacing: 0.175em;
}
</style>