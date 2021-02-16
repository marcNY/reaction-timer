<template>
  <p>Your score is {{score}}</p>
  <p>Your rank is {{rank}}</p>
</template>

<script>
export default {
  props: ["score"],
  computed: {
    rank() {
      if (this.score < 250) {
        return "ninja finger";
      } else if (this.score < 400) {
        return "Rapid Reflexes";
      } else {
        return "Snail Pace";
      }
    }
  }
};
</script>

<style>
</style>