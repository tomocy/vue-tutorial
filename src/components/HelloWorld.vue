<template>
  <div class="container">
    <div class="columns">
      <template v-for="(quote, i) in quotes">
        <div class="column" :key="i">
          <quote-item :quote="quote"></quote-item>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
import Quote from "../models/quote";
import QuoteItem from "./QuoteItem.vue";

export default {
  components: { QuoteItem },
  name: "HelloWorld",
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
