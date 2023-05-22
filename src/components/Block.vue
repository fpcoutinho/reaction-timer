<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me!</div>
</template>

<script>
export default {
  props: ["delay"],
  emits: ["reactionTime"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit("end", this.reactionTime)
    },
  },
}
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background-color: #e74d3cc7;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
