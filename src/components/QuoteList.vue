<template>
  <div class="columns">
    <template v-for="(quote, i) in quotes">
      <div class="column" :key="i">
        <quote-item :quote="quote"></quote-item>
      </div>
    </template>
  </div>
</template>

<script>
import QuoteItem from "./QuoteItem.vue";

export default {
  components: { QuoteItem },
  name: "QuoteList",
  props: {
    quotes: {
      type: Array,
      default: function () {
        return [];
      },
    },
  },
};
</script>