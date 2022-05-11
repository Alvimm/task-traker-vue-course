<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <StopWatch :timeInSeconds="timeInSeconds" />
    <button class="button" @click="start" :disabled="stopwatchRunning">
      <span class="icon"><i class="fas fa-play"></i></span><span>play</span>
    </button>
    <button class="button" @click="finish" :disabled="!stopwatchRunning">
      <span class="icon"><i class="fas fa-stop"></i></span><span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import StopWatch from './Stopwatch.vue';

export default defineComponent({
  name: 'TimerItem',
  emits: ['toTheTimerFinished'],
  components: {
    StopWatch,
  },
  data() {
    return {
      timeInSeconds: 0,
      stopwatch: 0,
      stopwatchRunning: false,
    };
  },
  methods: {
    start() {
      this.stopwatchRunning = true;
      this.stopwatch = setInterval(() => {
        this.timeInSeconds += 1;
      }, 1000);
    },
    finish() {
      this.stopwatchRunning = false;
      clearInterval(this.stopwatch);
      this.$emit('toTheTimerFinished', this.timeInSeconds);
      this.timeInSeconds = 0;
    },
  },
});
</script>
