<template>
  <div class="container">
    <MarkerLeft />
    <Countdown />
    <MarkerRight />
  </div>
</template>

<script>
import Countdown from "../src/components/Countdown";
import MarkerLeft from "../src/components/MarkerLeft";
import MarkerRight from "../src/components/MarkerRight";

export default {
  name: "App",
  components: {
    Countdown,
    MarkerLeft,
    MarkerRight,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  border-bottom: 0;
  overflow: hidden;
}

#app {
  font-family: Rajdhani, Helvetica, Arial, sans-serif;
  background: #f2f3f5;
}

.container {
  display: grid;
  height: 100vh;
  grid-template-columns: 1fr 1fr 1fr;
  justify-items: center;
  padding: 5px;
}
</style>
