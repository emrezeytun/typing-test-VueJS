<template>
  <div class="word-bar-container">
    <input v-model="wordInput" @input="inputChange" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      wordInput: ''
    }
  },  
  props: {
    isGameStarted: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    inputChange(e) {
      !this.isGameStarted && this.$emit('gameOptions', true)
      if(e.data === ' ' && this.wordInput.length > 0) this.wordInput = ''
      this.$emit('inputChange', e)
    },
  }
};
</script>

<style lang="scss" scoped>
.word-bar-container {
  margin-top: 12px;
  width: 100%;
  display: flex;
  justify-content: center;
  input {
    width: 90%;
    text-align: left;
    height: 36px;
    font-size: 16px;
    border-radius: 12px;
    border: 1px solid rgba(0,0,0,0.3);
    padding: 8px;
  }
  input:focus{
    outline: none;

}

}
</style>
