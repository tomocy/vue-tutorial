<template>
  <div class="card">
    <div class="card-content">
      <p class="title">
        {{ quotedBody }}
      </p>
      <p class="subtitle">{{ author }}</p>
    </div>
    <footer class="card-footer">
      <like-button :liked="liked"></like-button>
    </footer>
  </div>
</template>

<script>
import LikeButton from "./LikeButton.vue";

export default {
  components: { LikeButton },
  name: "QuoteItem",
  props: {
    author: {
      type: String,
      required: true,
    },
    body: {
      type: String,
      required: true,
    },
    liked: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    quotedBody() {
      if (this.body.startsWith('"') && this.body.endsWith('"')) {
        return this.body;
      }

      return `"${this.body}"`;
    },
  },
};
</script>