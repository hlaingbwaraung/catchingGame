<template>
  <div class="Block" v-if="showBlock" @click="stopTimer">Catch me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      score: 0,
      timer: null,
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
        this.score += 50;
      }, 50);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.score);
    },
  },
};
</script>

<style>
.Block {
  background-color: aquamarine;
  color: black;
  width: 150px;
  height: 150px;
  padding: 100px;
  margin: 120px auto;
}
</style>
