<template>
    <h3 class="results mt-5 color-primary">Reaction Time: {{reactionTime}} ms</h3>
    <p class="remark">{{ remark }}</p>
</template>

<style>
    .results{
        font-weight: 700;
        font-size: 2.5rem;
        color:rgb(72, 197, 72);
    }
</style>

<script>
export default {
    props:['reactionTime'],
    data(){
        return {
            remark:'',
        }
    },
    mounted(){
        if(this.reactionTime < 250){
            this.remark = 'Fast Reflexes'
        }
        else if(this.reactionTime < 400){
            this.remark = 'Good Reflexes, can be better'
        } else {
            this.remark = 'Slow Reflexes, Do Better!'
        }
    }
}
</script>
