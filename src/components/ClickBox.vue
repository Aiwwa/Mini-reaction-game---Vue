<template>
  <div class='click_box' v-if='showClickBox' @click='stopTimer'>
    Click me
  </div>
</template>

<script>

export default {
  props: ['delay'],
  data(){
    return {
      showClickBox: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted(){
    console.log('mounted')
    setTimeout(() => {
      this.showClickBox = true
      this.startTimer()
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    },
  }
}
</script>

<style>
  .click_box{
    width:200px;
    background-color: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 200px auto;
  }
</style>
