<template>
  <div class="block" v-if="showBlock" @click="endTimer">Click Me</div>
</template>

<script>
export default {
  data() {
    return { showBlock: false, timer: null, timeInterval: 0 };
  },
  props: ["delay"],
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => (this.timeInterval += 10), 10);
    },
    endTimer() {
      clearInterval(this.timer);
      this.showBlock = false;
      this.$emit("end", this.timeInterval);
    }
  }
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: rgb(130, 238, 130);
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>