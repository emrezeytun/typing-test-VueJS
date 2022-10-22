<template>
<div class="stats">
    <span class="stats-info stats-correct">Correct: {{counts.correct}} </span>  
    <span class="stats-info stats-wrong">Wrong: {{counts.wrong}}</span>
</div>  
</template>

<script>
export default {
    props: {
        counts: {
            type: Object,
            default: {
                correct: 0,
                wrong: 0
            }
        }
    }

}
</script>

<style lang="scss">
.stats {
    padding: 20px;
    &-info {
        color: #fff;
        padding: 8px;
    }
    &-correct {
        background-color: rgb(10, 112, 10);
        border-top-left-radius: 4px;
        border-bottom-left-radius: 4px;
    }
    &-wrong {
        background-color: rgb(209, 9, 9);
        border-bottom-right-radius: 4px;
        border-top-right-radius: 4px;
    }
}

</style>