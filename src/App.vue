<template>  
 <div>
    <h3 class='title'>PLAY REACTION GAME</h3>
    <button @click='startGame' :disabled='isPlaying' class='game-btn'>Start Game</button> 
    <ClickBox v-if='isPlaying' :delay='delay' @end='endGame'/>  
    <ResultCard v-if='showResult' :score='score'/>
  </div>
</template>

<script>
import ClickBox from './components/ClickBox.vue'
import ResultCard from './components/Results.vue'

export default {
  name: 'App',
  components: {
    ClickBox,
    ResultCard 
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    }
  },
  methods: {
    startGame(){
      this.delay = 1000 + Math.round(Math.random() * 3000)
      this.isPlaying = true
      this.showResult = false

    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  },
}
</script>

<style>
body {
    background-color:darkgray;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
  display:flex;
  flex-direction:column;
  align-items:center;
}

.title {
  color: white;
  font-weight:600;
  margin-bottom: 60px;
}

.game-btn {
  padding: 20px 30px;
  border-radius: 5px;
  background-color: #0faf87;
  color: white;
  border: none;
  -webkit-box-shadow: 7px 6px 35px -7px rgba(0,0,0,0.42); 
  box-shadow: 7px 6px 35px -7px rgba(0,0,0,0.42); 
}

button[disabled].game-btn {
  opacity: 0.2;
  cursor: not-allowed;
}

.playing {
  background-color:gray;
}
</style>
