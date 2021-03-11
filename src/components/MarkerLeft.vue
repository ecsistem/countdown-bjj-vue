<template>
  <div class="marker">
    <h1>Lutador 1</h1>
    <div style="border: 10px solid #5965e0; margin-bottom: 10px"></div>
    <Scores />
    <Buttons />
  </div>
</template>

<script>
import Scores from "./Scores";
import Buttons from "./Buttons";

export default {
  components: {
    Scores,
    Buttons,
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