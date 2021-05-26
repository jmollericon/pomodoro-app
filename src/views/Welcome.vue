<template>
  <section class="welcome">
    <div class="app-content welcome-content">
      <h1 class="welcome-title">Hello, ¡welcome to pomodoro!</h1>
      <h2 class="welcome-sutitle">Improve your productivity by focusing
        on what is important in each moment and be more efficient.
      </h2>
      <Button @click="onClick()">
        Make your first pomodoro
      </Button>
    </div>
  </section>
</template>

<script>
import Button from '@/components/Button.vue';

export default {
  name: 'Welcome',
  components: {
    Button,
  },
  methods: {
    onClick() {
      this.$router.push({ name: 'Pomodoro', params: { type: 'work' } });
    },
  },
};
</script>

<style lang="scss" scoped>
.welcome {
  background-color: var(--app-color-primary);
}
.welcome-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: var(--app-color-text);
}
.welcome-title {
  font-size: 2rem;
  font-weight: 500;
  letter-spacing: 1px;
  margin-bottom: 1.2rem;
}
.welcome-sutitle {
  font-size: 1.2rem;
  font-weight: 300;
  margin-bottom: 1.2rem;
}
</style>
