<template>
    <div @click="delQuote">
        <div class="quote-box"> {{ quote.value }} </div>
    </div>
</template>

<script>
import { QuotesBus } from '../main'
export default {
    props: ['quote'],
    methods: {
        delQuote(){
            QuotesBus.$emit('deleteQuote', this.quote);
        }
    }
}
</script>

<style scoped>
.quote-box{
    width: 19vw;
    height: 10vh;
    border: black 1px solid;
    float: left;
    margin: 1vh 1vw;
}
</style>