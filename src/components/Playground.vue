<template>
    <div class="block" v-if="showBlock" @click="stopPlaying">
        <h3>
            Click Here {{delay}}
        </h3>
    </div>
</template>

<script>
export default {
    name: 'Playground',
    props: ['delay'],
    data(){
        return {
            showBlock : false,
            timer : null,
            clickTime: 0
        }
    },
    
    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.startPlaying()
        },this.delay)
        console.log("mounted")
    },
    methods: {
        startPlaying(){
            this.timer = setInterval(()=>{
                this.clickTime += 10;
            }, 10)
        },
        stopPlaying(){
            clearInterval(this.timer);
            this.$emit('end',this.clickTime)
        }
    }
}
</script>

<style>
    .block{
        height: 200px;
        width: 200px;
        background: #ffc107;
        color: #fff;
        margin:40px auto;
        text-align: center;
        display: flex;
        align-items: center;
        border-radius: 9px;
    }
    .block h3{
        margin:auto;
    }
</style>