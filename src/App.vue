<template>
    <div class="container">
        <app-header :maxQuotes="maxQuotes" :quoteCount="quotes.length"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm12 text-center">
                <div class="alert alert-info">
                    Info: Click on a Quote to delete it
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Header from './components/Header.vue'
    import QuoteGrid from './components/QuoteGrid.vue'
    import NewQuote from './components/NewQuote.vue'
    export default {
        data: function () {
            return {
                quotes: [
                    'initial quote'
                ],
                maxQuotes: 10
            }
        },
        components: {
            appHeader: Header,
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote
        },
        methods: {
            newQuote(quote){
                if(this.quotes.length < this.maxQuotes){
                    this.quotes.push(quote);
                } else {
                    alert('please delete some quotes');
                }
            },
            deleteQuote(index) {
                this.quotes.splice(index,1);
            }
        }
    }
</script>

<style>
</style>
