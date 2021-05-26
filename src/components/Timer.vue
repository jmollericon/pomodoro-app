<template>
  <section>
    {{ minutes }}:{{ seconds }}
  </section>
</template>

<script>
export default {
  name: 'Timer',
  props: {
    time: {
      type: Number,
      default: 1200,
    },
  },
  data() {
    return {
      timeInSeconds: 0,
    };
  },
  mounted() {
    this.setTime(this.$props.time);
    this.startCounDown();
  },
  computed: {
    minutes() {
      const minutes = Math.floor(this.timeInSeconds / 60);
      return this.getPaddedTime(minutes);
    },
    seconds() {
      const seconds = Math.floor(this.timeInSeconds % 60);
      return this.getPaddedTime(seconds);
    },
  },
  methods: {
    startCounDown() {
      const onSecondElapse = window.setInterval(() => {
        if (!this.timeInSeconds) {
          window.clearInterval(onSecondElapse);
          return;
        }
        this.onSecondElapse();
      }, 1000);
    },
    onSecondElapse() {
      this.timeInSeconds -= 1;
    },
    setTime(time) {
      this.timeInSeconds = time;
    },
    getPaddedTime(value) {
      return value.toString().padStart(2, '0');
    },
  },
  watch: {
    time(newTime) {
      this.setTime(newTime);
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
