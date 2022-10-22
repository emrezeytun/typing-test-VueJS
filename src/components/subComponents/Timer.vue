<template>
    <div class="timer">
       <span class="timer-second">{{remainingTime}} Seconds</span>
    </div>  
    </template>
    
    <script>
    export default {
        data() {
            return {
                remainingTime: this.gameTime,
                gameInterval: null,
            }
        },  
        props: {
            gameTime: {
                type: Number,
                default: 60
            },
            isGameStarted: {
                type: Boolean,
                default: false
            }
        },
       
        watch: {
            isGameStarted() {
                this.isGameStarted && this.startGame()
            }
        },  
        methods: {
            startGame() {
                this.remainingTime = this.gameTime
                this.gameInterval = setInterval(() => {
                    this.timer()
                }, 1000)
            },
            timer() {
                console.log(this.remainingTime)
                 this.remainingTime--;
                if(this.remainingTime <= 0) this.stopGame()
            },  
            stopGame() {
                clearInterval(this.gameInterval)
                console.log('evet geldi')
                this.$emit('gameOptions', false)
            }
        },
        
        created() {
       
        }
    
    }
    </script>
    
    <style lang="scss">
    .timer {
        position: absolute;
        top:0;
        right: 0;
        padding: 8px;
        background-color: rgba(0,0,0,0.8);
        border-top-right-radius: 16px;
        &-second {
            color: #fff;
        }
    }
    
    </style>