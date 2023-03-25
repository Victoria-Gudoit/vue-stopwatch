<template>
<div class="app">
  <Stopwatch :timer="formattedTime" :state="timerState" @start="start" @pause="pause" @stop="stop"/>
</div>
</template>

<script>
import Stopwatch from '@/components/Stopwatch'
export default {
    components: {
        Stopwatch
    },
    data() {
      return {
         timerState: 'stopped',
      currentTimer: 0,
      formattedTime: "00:00:00",
      ticker: undefined,
      }
    },
    methods: {
      start() {
        if(this.timerState !== 'running') {
          this.tick();
        this.timerState = 'running';
        }
      },
      pause() {
        window.clearInterval(this.ticker)
        this.timerState = 'paused'
      },
      stop() {
        window.clearInterval(this.ticker)
        this.currentTimer = 0
        this.formattedTime = "00:00:00"
        this.timerState = 'stopped'
      },
      tick() {
        this.ticker = setInterval(() => {
          this.currentTimer++
          this.formattedTime = this.formatTime(this.currentTimer)
        }, 1000)
      },
      formatTime(seconds) {
        let measuredTime = new Date(null)
        measuredTime.setSeconds(seconds)
        let MHSTime = measuredTime.toISOString().substr(11, 8)
        return MHSTime
      }
    }
    }
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

button {
outline: none;
 background-color: transparent;
 border: none;
 cursor: pointer;
}

.app {
  background-color: #353638;
  height: 100vh;
}
</style>