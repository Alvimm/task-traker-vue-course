<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Form for creating a new task"
      >
        <input
          type="text"
          class="input"
          placeholder="Which task do you want to start?"
          v-model="description"
        />
      </div>
      <div class="column">
        <TimerItem @toTheTimerFinished="finishTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TimerItem from './Timer.vue';

export default defineComponent({
  name: 'FormItem',
  components: {
    TimerItem,
  },
  data() {
    return {
      description: '',
    };
  },
  methods: {
    finishTask(elapsedTime: number): void {
      console.log('Task time:', elapsedTime);
      console.log('Task description:', this.description);
      this.description = '';
    },
  },
});
</script>
