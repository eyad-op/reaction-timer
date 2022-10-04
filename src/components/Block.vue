<template>
  <div v-if="showBlock" @click="stopTimer" class="block">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("gameEnd", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 15rem;
  margin: 2rem auto;
  padding: 5rem 0;
  background: #0faaaf;
  border-radius: 0.5rem;
  color: aliceblue;
  font-size: 2rem;
  font-weight: bold;
  cursor: pointer;
}
</style>
