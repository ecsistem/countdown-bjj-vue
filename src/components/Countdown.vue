<template>
  <div class="countdown">
    <span>0</span>
    <span>5</span>
    <span>:</span>
    <span>0</span>
    <span>0</span>

    <div class="countdown-button">
      <button>Iniciar</button>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.countdown {
  display: block;
  width: 300px;
  margin-top: 30%;
  padding: 5px;
  text-align: center;
}

.countdown span {
  background: #fff;
  margin-right: 4px;
  padding: 5px;
  border-radius: 5px;
  font-family: Rajdhani;
  font-style: normal;
  font-weight: bold;
  font-size: 100px;
  color: #2e384d;
}

.countdown-button {
  margin-top: 50px;
}

.countdown-button button {
  filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
  background: #5965e0;
  color: #fff;
  padding: 10px;
  width: 100%;
  border: none;
  text-transform: uppercase;
  font-family: Rajdhani;
  font-style: normal;
  font-weight: bold;
  font-size: 25px;
  line-height: 32px;
  /* identical to box height */
  letter-spacing: 0.165em;
}

.countdown-button button:hover {
  background: #4953b8;
}
</style>