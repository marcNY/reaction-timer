<template>
  <button class="block" v-if="showBlock" @click="endTimer" v-bind:style="{top:ypos,left:xpos}"></button>
</template>

<script>
export default {
  data() {
    return { showBlock: false, timer: null, timeInterval: 0 , xpos: null, ypos: null};
  },
  props: ["delay"],
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);

    this.xpos=(Math.floor(Math.random()*100)).toString() + "%";
    this.ypos=(Math.floor(Math.random()*100)).toString() + "%";

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
  width: 5%;
  height: 5%;
  border-radius: 20px;
  background: rgb(130, 238, 130);
  color: white;
  text-align: center;
  position:absolute;
}
</style>