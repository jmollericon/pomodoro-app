<template>
  <section class="pomodoro">
    <div class="app-content pomodoro-content">
      <Timer :time="pomodoroTime"/>
    </div>
  </section>
</template>

<script>
import Timer from '@/components/Timer.vue';
import PomodoroTypes from './pomodoroTypes';

export default {
  name: 'Pomodoro',
  components: {
    Timer,
  },
  computed: {
    pomodoroTime() {
      const pomodoroType = this.$route.params.type;
      return PomodoroTypes[pomodoroType].time;
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
