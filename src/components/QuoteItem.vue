<template>
  <div class="card">
    <div class="card-content">
      <p class="title" v-text="quote.body"></p>
      <p class="subtitle" v-text="quote.author"></p>
    </div>
    <footer class="card-footer">
      <like-button :liked="quote.liked"></like-button>
    </footer>
  </div>
</template>

<script>
import Quote from "../models/quote";
import LikeButton from "./LikeButton.vue";

export default {
  components: { LikeButton },
  name: "QuoteItem",
  props: {
    quote: {
      type: Quote,
      required: true,
    },
  },
  computed: {
    quotedBody() {
      if (this.quote.body.startsWith('"') && this.quote.body.endsWith('"')) {
        return this.quote.body;
      }

      return `"${this.quote.body}"`;
    },
  },
};
</script>