<template>
    <div class="container">
        <appHeader :quoteCount="arrayOfQuotes.length" :maxQuotes="maxQuotes"></appHeader>
        <appNewQuote @quoteAdded="newQuote"></appNewQuote>
        <appAllQuotes :quotes="arrayOfQuotes" @quoteDeleted="deleteQuote"></appAllQuotes>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Click on a quote to delete it
                </div>

            </div>
        </div>
    </div>
</template>

<script>
    import Header from "./components/Header";
    import NewQuote from "./components/NewQuote";
    import AllQuotes from "./components/AllQuotes";
    import SingleQuote from "./components/SingleQuote";

    export default {
        data() {
            return {
                maxQuotes: 10,
                arrayOfQuotes: ['Just a quote to see something'],
            }
        },

        components: {
            appHeader: Header,
            appNewQuote: NewQuote,
            appAllQuotes: AllQuotes,
            appSingleQuote: SingleQuote
        },

        methods: {
            newQuote(quote) {
                if (this.arrayOfQuotes.length + 1 > this.maxQuotes) {
                   return alert("You have reach the max number of quotes limit!  Delete some to add new ones")
                } else {
                    this.arrayOfQuotes.push(quote);
                }
            },
            deleteQuote(index) {
                this.arrayOfQuotes.splice(index, 1);
            },
            checkQuoteCount(maxNumber) {

            }
        }
    }
</script>

<style>
</style>
