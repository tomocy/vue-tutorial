<template>
  <div class="container">
    <quote-list :quotes="quotes"></quote-list>
  </div>
</template>

<script>
import Quote from "../models/quote";
import QuoteList from "./QuoteList";

export default {
  name: "HelloWorld",
  components: {
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
};
</script>

<style scoped>
</style>
