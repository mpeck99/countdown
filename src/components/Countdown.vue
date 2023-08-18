<template>
  <div class="inner">
    <div class="countdown-wrapper">
      <p>
        <span class="time">{{ days }}</span> <span class="label">Days</span>
      </p>

      <p>
        <span class="time">{{ hours }}</span> <span class="label">Hours</span>
      </p>

      <p>
        <span class="time">{{ mins }}</span
        ><span class="label">Minutes</span>
      </p>

      <p>
        <span class="time">{{ secs }}</span> <span class="label">Seconds</span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    days: 0,
    hours: 0,
    mins: 0,
    secs: 0
  }),
  computed: {
    _seconds: () => 1000,
    _minutes() {
      return this._seconds * 60
    },
    _hours() {
      return this._minutes * 60
    },
    _days() {
      return this._hours * 24
    }
  },
  mounted() {
    this.showRemaining()
  },
  methods: {
    formatNum: (num) => (num < 10 ? '0' + num : num),
    showRemaining() {
      const timer = setInterval(() => {
        const today = new Date()
        const endDate = new Date(2023, 12, 11, 0, 0, 0)
        const distance = endDate.getTime() - today.getTime()

        if (distance < 0) {
          clearInterval(timer)
          return
        }

        const days = Math.floor(distance / this._days)
        const hours = Math.floor((distance % this._days) / this._hours)
        const minutes = Math.floor((distance % this._hours) / this._minutes)
        const seconds = Math.floor((distance % this._minutes) / this._seconds)

        this.mins = this.formatNum(minutes)
        this.secs = this.formatNum(seconds)
        this.hours = this.formatNum(hours)
        this.days = this.formatNum(days)
      }, 1000)
    }
  }
}
</script>

<style scoped lang="scss">
.inner {
  height: 100%;

  display: flex;
  justify-content: center;
  align-items: center;

  margin: 0 auto;
}

.countdown-wrapper {
  max-width: 75vw;

  display: flex;
  flex-direction: column;

  padding: clamp(2rem, 0.909rem + 5.45vw, 5rem);

  border: 0.2rem solid #fff;
  border-radius: 2rem;

  box-shadow: 0 0 0.2rem #fff, 0 0 0.2rem #fff, 0 0 2rem #892cdc, 0 0 0.8rem #892cdc,
    0 0 2.8rem #892cdc, inset 0 0 1.3rem #892cdc;

  p {
    text-align: center;

    .label {
      font-size: clamp(1.125rem, 0.807rem + 1.59vw, 2rem);
      text-align: center;

      color: #3eff15;
    }
  }

  @media (min-width: 768px) {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 100%;
    gap: 1rem;
  }
}

.time {
  height: 100%;

  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;

  font-family: 'Bruno Ace SC', cursive;
  font-size: clamp(5rem, 3.909rem + 5.45vw, 8rem);

  color: #fff;
  text-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff, 0 0 42px #f09, 0 0 82px #f09,
    0 0 92px #f09, 0 0 102px #f09, 0 0 151px #f09;

  animation: pulsate 0.11s ease-in-out infinite alternate;
}

@keyframes pulsate {
  100% {
    text-shadow: 0 0 4px #fff, 0 0 11px #fff, 0 0 19px #fff, 0 0 40px #f09, 0 0 80px #f09,
      0 0 90px #f09, 0 0 100px #f09, 0 0 150px #f09;
  }

  0% {
    text-shadow: 0 0 4px #fff, 0 0 10px #fff, 0 0 18px #fff, 0 0 38px #f09, 0 0 73px #f09,
      0 0 80px #f09, 0 0 94px #f09, 0 0 140px #f09;
  }
}
</style>