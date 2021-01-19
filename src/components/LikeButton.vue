<template>
  <button @click="toggle" :class="classes" v-text="text"></button>
</template>

<script>
export default {
  name: "LikeButton",
  props: {
    liked: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      active: this.liked,
    };
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
};
</script>