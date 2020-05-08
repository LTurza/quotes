<template>
    <div class="bg">
        <slot name="title"></slot>
        <textarea name="" id="" cols="100" rows="5" v-model="quote"></textarea>
        <br>
        <button class="btn btn-primary" @click="this.addQuotes"> Add Quote</button>
        <h3>Your Quote's:</h3>
        <app-quotes-grid v-for="q in quotes" :key="q.id" :quote = "q" >
            
        </app-quotes-grid>
    </div>
</template>

<script>
import { QuotesBus } from "./../main";
import QuotesGridVue from './QuotesGrid.vue';
export default {
    
    data: function(){
        return{
            quotes: [],
            quote: '',
            quoteId: 0
        }
    },
    methods: {
        addQuotes(){
            if(this.quotes.length === 10){
                window.alert('you have to many quotes. Delete some of them to make a space for another quotes');
            }
            else{
            this.quoteId++;
            QuotesBus.$emit('numberOfQuotes', this.quotes.length+1);
            this.quotes.push({id: this.quoteId, value: this.quote});
            }
        }
    },
    components: {
        appQuotesGrid: QuotesGridVue
    },
    created(){
        QuotesBus.$on('deleteQuote', (data) => {
            this.quotes.splice(this.quotes.indexOf(data),1);
            QuotesBus.$emit('numberOfQuotes', this.quotes.length);

        });
    }
}
</script>

<style scoped>
.bg{
    margin-left: 10vw;
}
textarea{
    border-radius: 5px;
}
button{
    margin-left: 35vh;
}

</style>