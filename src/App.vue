<template>
    <div class="container">
        <app-quote-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-quote-header>
        <app-new-quote @quoteAdded="newQuote($event)"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';

    export default {
        data: function() {
            return {
                quotes: [
                    'Sample Quote'
                ],
                maxQuotes: 10
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appQuoteHeader: Header,
            appNewQuote: NewQuote
        },
        methods: {
            newQuote(quote) {
                if (this.quotes.length >= this.maxQuotes){
                    return alert('please delete quotes first');
                }
                this.quotes.push(quote);
            },
            deleteQuote(index) {
                this.quotes.splice(index, 1);
            }
        }
    }
</script>

<style>
</style>
