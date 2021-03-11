<template>
  <div class="countdown">
    <span>{{ minuteLeft }}</span>
    <span>{{ minuteRight }}</span>
    <span>:</span>
    <span>{{ secondLeft }}</span>
    <span>{{ secondRight }}</span>

    <div class="countdown-button">
      <button v-on:click="startCountdown()">Iniciar</button>
    </div>
  </div>
</template>

<script>
let time = 0.2 * 60;
let minute = null;
let seconds = null;

let isActive = false;

let [minuteLeft, minuteRight] = [0, 5];
let [secondLeft, secondRight] = [0, 0];

let idSetTime;

export default {
  methods: {
    startCountdown: function () {
      isActive = true;
      console.log(time);
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
        console.log(time);
        console.log(
          minuteLeft + minuteRight + " : " + secondLeft + secondRight
        );
        if (time === 0) {
          clearInterval(idSetTime);
          console.log("Acabou o tempo.");
        }
      }, 1000);
    },
  },
  data: function () {
    return {
      minute,
      seconds,
      minuteLeft,
      minuteRight,
      secondLeft,
      secondRight,
      isActive,
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