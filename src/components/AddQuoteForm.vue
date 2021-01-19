<template>
  <div class="hero is-light">
    <form @submit.prevent="onSubmit" @keydown="onKeydown($event.target.name)">
      <div class="hero-body">
        <div class="field">
          <label class="label">Author</label>
          <div class="control">
            <input class="input" type="text" name="author" v-model="author" />
          </div>

          <p
            v-show="authorError"
            class="help is-danger"
            v-text="authorError"
          ></p>
        </div>

        <div class="field">
          <label class="label">Body</label>
          <div class="control">
            <input
              class="input is-success"
              type="text"
              name="body"
              v-model="body"
            />
          </div>

          <p v-show="bodyError" class="help is-danger" v-text="bodyError"></p>
        </div>

        <div class="control">
          <button class="button is-primary">Add</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddQuoteForm",
  data() {
    return {
      author: "",
      authorError: null,
      body: "",
      bodyError: null,
    };
  },
  methods: {
    onKeydown(field) {
      if (field === "author") {
        this.authorError = "";
        return;
      }

      if (field === "body") {
        this.bodyError = "";
        return;
      }
    },
    onSubmit() {
      if (!this.validate()) {
        return false;
      }

      this.$emit("add", this.author, this.body);

      this.author = "";
      this.authorError = null;
      this.body = "";
      this.bodyError = null;

      return true;
    },
    validate() {
      let valid = true;

      if (this.author === "") {
        this.authorError = "The author is empty";
        valid = false;
      }

      if (this.body === "") {
        this.bodyError = "The body is empty";
        valid = false;
      }

      return valid;
    },
  },
};
</script>