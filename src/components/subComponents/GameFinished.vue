<template>
  <div class="game-finished">
    <div class="game-finished-game-over">
        <p > <span>{{gameOverDescription}}</span> </p>
    </div>

    <div class="game-finished-game-stats">
        <p>  Correct: <span>{{counts.correct}}</span>   Wrong: <span>{{counts.wrong}}</span>  </p>
    </div>
 
    
    <div class="game-finished-start-again">  <button @click="startAgain">Start Again</button></div>
  
  </div>
</template>

<script>

export default {
    props: {
        gameOverDescription: {
            type: String,
            default: "Game over."
        },
        counts: {
            type: Object,
            default: {
                correct: 0,
                wrong: 0
            }
        }
    },
    methods: {
        startAgain() {
            this.$emit('gameOptions', true)
        }
    }

}
</script>

<style lang="scss" scoped>
.game-finished {
    display: flex;
    justify-content: center;
    flex-direction: column;
    &-game {
    &-over {
        justify-content: center;
        display: flex;
        width: 100%;
        p {
        width: max-content;
        justify-content: center;
        display: flex;
        background-color: red;
        border-radius: 12px;
        padding: 12px;
        }
        span {
            color: #fff;
        }
    }
    &-stats {
        justify-content: center;
        display: flex;
        width: 100%;
        p {
        width: max-content;
        justify-content: center;
        display: flex;
        background-color: rgba(0,0,0,0.8);
        border-radius: 12px;
        padding: 12px;
        color: #fff !important;
        margin-bottom: 32px;
        }
        span {
            margin-right: 8px;
            margin-left: 4px;
        }
    } }
    span {
        font-weight: 600;
    }
    p {
        text-align: center;
        color: rgba(0,0,0,0.7)
    }
    &-start-again {
        justify-content: center;
        display: flex;
            button {
            background-color: #1895a8;
            color: #fff;
            border: none;
            width: fit-content;
            padding: 12px;
            cursor: pointer;
            }
    }
   
}

</style>