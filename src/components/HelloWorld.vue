<template>
  <div class="container">
    <div class="section">
      <quote-list :quotes="quotes"></quote-list>
      <add-quote-form @add="addQuote"></add-quote-form>
    </div>
  </div>
</template>

<script>
import Quote from "../models/quote";
import AddQuoteForm from "./AddQuoteForm.vue";
import QuoteList from "./QuoteList";

export default {
  name: "HelloWorld",
  components: {
    AddQuoteForm,
    QuoteList,
  },
  data() {
    return {
      quotes: [
        new Quote(
          "Jeff Atwood",
          "There are two hard things in computer science: cache invalidation, naming things, and off-by-one errors."
        ),
        new Quote("Jeff Atwood", "ra ri ru re ro", true),
      ],
    };
  },
  methods: {
    addQuote(author, body) {
      const quote = new Quote(author, body);
      this.quotes.push(quote);
    },
  },
};
</script>

<style scoped>
</style>
