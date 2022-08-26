<template>
    <div class="result">
        <p class="text-green">
                Your Score is: {{endTime}}
        </p>
        <h1>
            {{rank}}
        </h1>
        
    </div>
</template>

<script>
export default {
    props:['endTime'],
    data(){
        return {
            rank : null
        }
    },
    mounted(){
        if(this.endTime < 250){
            this.rank = 'Ninja Fingers'
        }
        else if(this.endTime < 450 ){
            this.rank = 'Rapid Bro..'
        }
        else{
            this.rank = 'Merely Fast ...'
        }
    },
    unmount(){
        this.rank = null
    }
}
</script>

<style>
.result{
    padding: 15px 45px;
    
}
.result h1{
color: #28a745;
}
</style>