<template>
  <div class="container">
    <GameDescription v-if="!isGameFinished" :gameInformation="gameInformation" />
    <div v-if="!isGameFinished">
      <Words ref="words" @nextWord="(answer) => nextWord(answer)" :wordDatas="shuffleDatas" :typingWord="typingWord" />
    <WordBar @gameOptions="gameOptions" :isGameStarted="isGameStarted" @inputChange="inputChange" />
    </div>
    <div v-else>
      <GameFinished @gameOptions="gameOptions" :counts="counts" :gameOverDescription="gameInformation.gameOverDescription" />
    </div>
   
    <div v-if="!isGameFinished" class="container-timer-and-stats">
      <Timer @gameOptions="gameOptions" :gameTime="gameTime" :isGameStarted="isGameStarted" />
      <Stats :counts="counts" />
    </div>
 
  </div>
</template>

<script>
import {Words, WordBar, GameDescription, Stats, Timer, GameFinished} from '@/components/subComponents'
import {gameInformation, wordDatas, gameSettings} from '@/assets/datas/index'
export default {
  name: "Container",
  components: { Words, WordBar, GameDescription, Stats, Timer, GameFinished },
  data() {
    return {
      wordDatas,
      shuffleDatas: [],
      typingWord: null,
      gameInformation,
      isGameStarted: false,
      counts: {
        correct: 0,
        wrong: 0
      },
      gameTime: gameSettings.gameTime,
      remainingTime: gameSettings.gameTime
    }
  },

  created() {
   this.shuffleWords()
    console.log(this.shuffleDatas)
  },

  computed: {
       isGameFinished() {
       return this.remainingTime <= 0
         }
    },
   
  methods: {
    shuffleWords() {
      this.shuffleDatas = this.wordDatas.sort(() => .5 - Math.random()).slice(0,30);
    },
    inputChange(e) {
      this.typingWord = e
    },
    nextWord(answer) {
      console.log(answer)
      answer ? this.counts.correct++ : this.counts.wrong++
      this.shuffleDatas.shift()
      this.shuffleDatas = [...this.shuffleDatas, this.wordDatas[Math.floor(Math.random() * (this.wordDatas.length-1))]]
    },
    gameOptions(gameStatus = false) {
      console.log(gameStatus)
      this.isGameStarted = gameStatus
      !gameStatus ? this.remainingTime = 0 : this.resetGame()
    },
    resetGame() {
      this.remainingTime = this.gameTime
      this.counts = {wrong: 0, correct: 0}
    }
  
  }
};

</script>

<style lang="scss" scoped>
.container {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 50vw;
  padding: 20px;
  background-color: #fff;
  color: #fff;
  border-radius: 16px;
  &-timer-and-stats {
    display: flex;
    justify-content: flex-end;
  }
 
}
</style>

