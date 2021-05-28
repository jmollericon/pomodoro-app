<template>
  <section class="pomodoro">
    <div class="app-content pomodoro-content">
      <h2 class="pomodoro-title">Pomodoro</h2>
      <h1 class="pomodoro-type">{{ pomodoroType }}</h1>
      <Timer :time="pomodoroTime" class="pomodoro-timer"/>
      <RoundedButton @click="onClick()" class="icon-close">
        x
      </RoundedButton>
    </div>
  </section>
</template>

<script>
import Timer from '@/components/Timer.vue';
import RoundedButton from '@/components/RoundedButton.vue';
import PomodoroTypes from './pomodoroTypes';

export default {
  name: 'Pomodoro',
  components: {
    Timer,
    RoundedButton,
  },
  computed: {
    pomodoroType() {
      return this.$route.params.type;
    },
    pomodoroTime() {
      return PomodoroTypes[this.pomodoroType].time;
    },
    pomodoroNextUrl() {
      return PomodoroTypes[this.pomodoroType].next_url;
    },
  },
  methods: {
    onClick() {
      if (this.pomodoroNextUrl === 'rest') {
        this.$router.push({ name: 'Pomodoro', params: { type: 'rest' } });
      } else {
        this.$router.push({ name: 'Welcome' });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.pomodoro {
  background-color: var(--app-color-primary);
  color: var(--app-color-text);
}
.pomodoro-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.pomodoro-title {
  font-size: 1.2rem;
  font-weight: 300;
  text-transform: uppercase;
}
.pomodoro-type {
  font-size: 4rem;
  font-weight: 500;
  letter-spacing: 1px;
  margin-bottom: 1.2rem;
  text-transform: uppercase;
}
.pomodoro-timer {
  font-size: 8rem;
  font-weight: 800;
  margin-bottom: 3rem;
}
.icon-close {
  font-size: 4rem;
}
</style>
