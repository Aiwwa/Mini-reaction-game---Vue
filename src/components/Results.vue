<template>
  <div class='result_card'> 
    <div >Reaction time: <strong>{{this.score}} ms</strong></div>  
    <p class='rank'>{{rank}}</p>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: ''
    }
  },
  mounted() {
    if(this.score < 250) {
      this.rank = 'Speed of light'
    } else if(this.score < 400) {
      this.rank = 'Finished your coffee and try again'
    } else {
      this.rank = 'You need coffee !!!'
    }
  }
}
</script>


<style>
  .result_card {
    margin-top: 400px;
    padding: 30px 50px;
    background: #383122;
    color:white;
    align-items: center;
    max-width:300px;
    font-weight: 600;
    border-radius: 8px;
  }

  .rank {
    margin-top: 50px;
    color: #ffb300;
  }
</style>
