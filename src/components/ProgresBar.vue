<template>
    <div>
        <slot name="title"></slot>
        <div class="back-progress-bar">
             <div class="progress-bar" :style="{ width: countWidth + 'vw' }"> {{ amountOfQuotes }}/10</div>
        </div>
    </div>
</template>

<script>
import { QuotesBus } from "./../main";
export default {
    data: function(){
        return{
            amountOfQuotes: 0
        }
    },
    computed:{
        countWidth(){
            return 8 * this.amountOfQuotes;
        }
    },
    created() {
        QuotesBus.$on('numberOfQuotes', (data) => {
            this.amountOfQuotes = data;
        })
    }
    
}
</script>

<style scoped>
.progress-bar{
    width: 80vw;
    height: 3vh;
    border-radius: 5px;
    margin-left: 0.1vw;
    margin-top: 0.1vh;
}
.back-progress-bar{
    width: 80.2vw;
    height: 3.2vh;
    border-radius: 5px;
    margin: 0 -5.1vw !important;
    background-color: grey;
}
</style>