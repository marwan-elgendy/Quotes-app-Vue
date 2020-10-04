<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <new-quote @quoteAdded="check"></new-quote>
        <app-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-grid>
        <div cl ass="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a Quote to delete it. 
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import NewQuote from './components/NewQuote';
import QuoteGrid from './components/QuoteGrid'; 
import Header from './components/Header';
    export default {
        data(){
            return{
                quotes:[
                    'Just a Quote to see something',
                    'Test Quote'
                ],
                maxQuotes: 10,
            }
        },
        components:{
            appGrid : QuoteGrid,
            newQuote: NewQuote,
            appHeader: Header
        },
        methods:{
            check(quote){
                 if(this.quotes.length >= this.maxQuotes){
                    alert('Please Delete Quotes first.');
                }
                else{
                    this.newQuote(quote);
                }
            },
            newQuote(quote){
                this.quotes.push(quote);
            },
            deleteQuote(index){
                this.quotes.splice(index, 1);
            }
        }
    }
</script>

<style>
</style>
