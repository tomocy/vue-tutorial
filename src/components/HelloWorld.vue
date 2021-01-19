<template>
  <div class="container">
    <div class="columns">
      <div class="column">
        <quote-item
          author="Jeff Atwood"
          body="There are two hard things in computer science: cache invalidation, naming things, and off-by-one errors."
        ></quote-item>
      </div>
      <div class="column">
        <quote-item
          author="Jeff Atwood"
          body='"ra ri ru re ro"'
          liked
        ></quote-item>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteItem from "./QuoteItem.vue";

export default {
  components: { QuoteItem },
  name: "HelloWorld",
  data() {
    return {};
  },
};
</script>

<style scoped>
</style>
