<template>
  <button @click="toggle" :class="classes" v-text="text"></button>
</template>

<script>
export default {
  name: "LikeButton",
  data() {
    return {
      active: false,
    };
  },
  props: {
    liked: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    classes() {
      return [
        "button",
        "is-primary",
        "is-fullwidth",
        this.active ? "" : "is-outlined",
      ];
    },
    text() {
      return this.active ? "Liked" : "Like";
    },
  },
  methods: {
    toggle() {
      this.active = !this.active;
    },
  },
  created() {
    this.active = this.liked;
  },
};
</script>