<template>
  <div class="container-description">
      <h1>{{gameInformation.title}}</h1>
      <p>{{gameInformation.description}}
      </p>
    </div>
</template>

<script>
export default {
    props: {
        gameInformation: {
            type: Object,
            default: {}
        }
    }

}
</script>

<style lang="scss" scoped>
 .container-description {
    text-align: center;
    padding: 12px;
    h1 {
      color: rgba(0,0,0,0.7);
      margin: 0 0 8px 0;
      padding: 0;
    }
    p {
      color: rgba(0,0,0,0.7);
      margin: 0;
      padding: 0;
    }
    
  }
</style>