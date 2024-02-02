<template >

    <div ref="boxRef"  class="box" @click="stopTimer" :class="{green:turnColor}">
        Once green Click Here! Be ready. 
    </div>
</template>

<script>


    export default {
        name:'Block',
        props:['delay'],
        mounted(){
            setTimeout(()=>{
                this.turnColor = true
            },this.delay)
        },
        updated(){
            this.timer = setInterval(()=>{this.reactionTime+=5},5)
        },
        methods:{
            stopTimer(){
                if(this.$refs.boxRef.classList.contains('green')){
                    clearInterval(this.timer)
                    this.$emit('end',this.reactionTime)
                }
            }
        },
        data(){
            return{ 
                turnColor: false,
                timer:null,
                reactionTime:0
            }
        }
    }
</script>

<style scoped>
    .box{
        width:600px;
        height:200px;
        background-color: #333;
        color:white;
        border-radius: 16px;
        padding:1rem;
        text-align:center;
        margin:1rem auto;
        cursor:pointer;
    }
    .green{
        background-color: lightgreen;
    }
</style>