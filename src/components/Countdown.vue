<template>
  <div class="countdown">
    <span>{{ minuteLeft }}</span>
    <span>{{ minuteRight }}</span>
    <span>:</span>
    <span>{{ secondLeft }}</span>
    <span>{{ secondRight }}</span>

    <div class="countdown-button">
      <button v-on:click="startCountdown()" v-if="isActive === null">
        Iniciar
      </button>
      <button v-on:click="pauseCountdown()" v-else-if="isActive">Pausar</button>
      <button v-on:click="startCountdown()" v-else>Retomar</button>
    </div>
  </div>
</template>

<script>
let time = 0.2 * 60;
let minute = Math.floor(time / 60);
let seconds = time % 60;
let isActive = null;

let [minuteLeft, minuteRight] = String(minute).padStart(2, "0").split("");
let [secondLeft, secondRight] = String(seconds).padStart(2, "0").split("");

let idSetTime;

export default {
  methods: {
    pauseCountdown: function () {
      clearInterval(idSetTime);
      this.isActive = false;
    },
    startCountdown: function () {
      this.isActive = true;
      idSetTime = setInterval(() => {
        time = time - 1;
        minute = Math.floor(time / 60);
        seconds = time % 60;
        [minuteLeft, minuteRight] = String(minute).padStart(2, "0").split("");
        [secondLeft, secondRight] = String(seconds).padStart(2, "0").split("");
        this.minuteLeft = minuteLeft;
        this.minuteRight = minuteRight;
        this.secondLeft = secondLeft;
        this.secondRight = secondRight;

        if (time === 0) {
          clearInterval(idSetTime);
          this.isActive = null;
          time = 0.2 * 60;
        }
      }, 1000);
    },
  },
  data: function () {
    return {
      isActive,
      minute,
      seconds,
      minuteLeft,
      minuteRight,
      secondLeft,
      secondRight,
      idSetTime,
    };
  },
};
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