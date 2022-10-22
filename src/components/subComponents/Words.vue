<template>
  <div class="words-container">
    <span :class="index === 0 && dynamicClassForWord()" class="words-container-single-word " v-for="(word,index) in wordDatas" :key="index">
    {{word}}
    </span>
  </div>
</template>

<script>
export default {
    name: 'Words',
    data() {
        return {
            isTypingWrong: false
        }
    },  
    props: {
        wordDatas: {
            type: Array,
            default: []
        }, 
        typingWord: {
            type: InputEvent,
            default: null
        }
    },

    watch: {
        typingWord(e) {
            (e.data === ' ' && this.checkWord()) ? this.$emit('nextWord', true) : (e.data === ' ' && !this.checkWord()) && this.$emit('nextWord', false)
            this.checkWord(e.target.value, 'typing') ? this.isTypingWrong=false : this.isTypingWrong=true
            if(e.data === ' ' && this.checkWord(e.target.value, 'finishing') )  this.isTypingWrong=true
        }
    },

    methods: {
        dynamicClassForWord() {
          return  (this.isTypingWrong) ? 'words-container-false' : 'words-container-typing' 
        },
        checkWord( val = this.typingWord.target.value, type = 'finishing') {
            if(type === 'typing') return this.wordDatas[0].slice(0,val.length).toLowerCase() === val.toLowerCase()
            else {
                this.wordDatas[0].toLowerCase() === val.toLowerCase().split(' ')[0] ? this.isTypingWrong = true : this.isTypingWrong = false
                return this.wordDatas[0].toLowerCase() === val.toLowerCase().split(' ')[0]

            }
        
        }
    },
}
</script>

<style lang="scss" scoped>
.words-container {
    color: rgba(0,0,0,0.8);
    padding: 16px;
    border: 1px solid rgba(0,0,0,0.1);
    &-single-word {
            line-height: 30px;
            margin: 0px 4px 0px 4px;
            padding: 4px;
    }
    &-typing {
        background-color: rgb(73, 73, 73);
        color: #fff;
        border-radius: 4px;
    }
    &-false {
        background-color: red;
        color: #fff;
        border-radius: 4px;
    }
}

</style>