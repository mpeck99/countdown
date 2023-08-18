<template>
  <div class="inner">
    <div class="countdown-wrapper">
      <p>
        <span class="time">{{ days }}</span> <span class="label">Day</span>
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
  })
}
</script>

<style scoped lang="scss">
.inner {
  widows: 100%;
  height: 100%;

  display: flex;
  justify-content: center;
  align-items: center;

  margin: 0 auto;
}

.countdown-wrapper {
  display: flex;
  align-items: center;
  gap: 4rem;

  padding: 2rem;

  p {
    display: grid;
    grid-template-rows: 5rem 1fr;
    grid-template-columns: 100%;

    justify-content: center;
    align-items: center;

    .label {
      font-size: 2rem;
    }

    &:last-of-type .time::after {
      display: none;
    }
  }
}

.time {
  height: 5rem;

  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;

  grid-row: 1;

  font-family: 'Alumni Sans Inline One', cursive;
  font-size: 8rem;

  &::after {
    content: ':';

    position: absolute;
    right: -2.5rem;

    font-family: 'Roboto Condensed', sans-serif;
    font-size: 4rem;
  }
}
</style>