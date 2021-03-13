<template>
  <div class="countdown">
    <div class="countdown-times">
      <div>
        <p>Tempo de luta:</p>
      </div>
      <div>
        <input
          @click="editTime(5)"
          type="radio"
          v-model="selectedTime"
          value="5"
          checked
        />
        <label>05:00</label>
      </div>
      <div>
        <input
          @click="editTime(8)"
          type="radio"
          v-model="selectedTime"
          value="8"
        />
        <label>08:00</label>
      </div>
      <div>
        <input
          @click="editTime(10)"
          type="radio"
          v-model="selectedTime"
          value="10"
        />
        <label>10:00</label>
      </div>
    </div>
    <div>
      <span>{{ minuteLeft }}</span>
      <span>{{ minuteRight }}</span>
      <span>:</span>
      <span>{{ secondLeft }}</span>
      <span>{{ secondRight }}</span>
    </div>
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
let selectedTime = 5;
let time = selectedTime * 60;
let minute = Math.floor(time / 60);
let seconds = time % 60;
let isActive = null;

let [minuteLeft, minuteRight] = String(minute).padStart(2, "0").split("");
let [secondLeft, secondRight] = String(seconds).padStart(2, "0").split("");

let idSetTime;

export default {
  methods: {
    editTime: function (valorTime) {
      selectedTime = valorTime;
      time = selectedTime * 60;
      minute = Math.floor(time / 60);
      seconds = time % 60;
      [minuteLeft, minuteRight] = String(minute).padStart(2, "0").split("");
      [secondLeft, secondRight] = String(seconds).padStart(2, "0").split("");
      this.minuteLeft = minuteLeft;
      this.minuteRight = minuteRight;
      this.secondLeft = secondLeft;
      this.secondRight = secondRight;
    },
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
      selectedTime: 5,
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

.countdown-times {
  margin: 10px;
  display: flex;
  justify-content: space-between;
}

.countdown-times input {
  margin-right: 5px;
}

.countdown-times p {
  text-align: left;
}
</style>