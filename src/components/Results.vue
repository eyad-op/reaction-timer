<template>
  <p>Your reaction time is: {{ score }} ms</p>
  <p>{{ rank }}</p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja";
    } else if (this.score < 400) {
      this.rank = "Swifty";
    } else {
      this.rank = "Turtle";
    }
  },
};
</script>

<style>
p {
  font-weight: 600;
  font-size: 1.2rem;
}
</style>
