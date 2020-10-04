<template>
   <div class="row">
       <single-quote v-for="(quote,index) in quotes" :key="index" @click.native="deleteQuote">{{quote}}</single-quote>
   </div>
</template>

<script>
import Quote from './Quote'
export default {
    props:['quotes'],
    components:{
        singleQuote: Quote
    },
    methods:{
        deleteQuote(index){
            this.$emit('quoteDeleted', index);
        }
    }
}
</script>

<style>

</style>