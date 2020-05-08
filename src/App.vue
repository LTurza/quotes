<template>
    <div class="container">
    <app-progres-bar>
        <h1 slot="title">Quotes Added</h1>
    </app-progres-bar>

    <app-quotes-area>
        <h4 slot="title"> Quotes</h4>
    </app-quotes-area>
    </div>
</template>

<script>
import ProgresBarVue from './components/ProgresBar.vue'
import QuotesAreaVue from './components/QuotesArea.vue'
    export default {
        components: {
            appProgresBar: ProgresBarVue,
            appQuotesArea: QuotesAreaVue
        }
    }
</script>

<style>
</style>
