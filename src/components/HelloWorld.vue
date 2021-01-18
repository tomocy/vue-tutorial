<template>
  <div class="hello container">
    <form
      @submit.prevent="onSubmit"
      @keydown="form.errors.clear($event.target.name)"
    >
      <div class="field">
        <label class="label">Name</label>
        <div class="control">
          <input name="name" class="input" type="text" v-model="form.name" />
        </div>
        <p
          class="help is-danger"
          v-if="form.errors.doHave('name')"
          v-text="form.errors.get('name')"
        ></p>
      </div>
      <div class="field">
        <label class="label">Description</label>
        <div class="control">
          <input
            name="description"
            class="input"
            type="text"
            v-model="form.description"
          />
        </div>
        <p
          class="help is-danger"
          v-if="form.errors.doHave('description')"
          v-text="form.errors.get('description')"
        ></p>
      </div>
      <div class="control">
        <button
          :disabled="!form.canSubmit()"
          :class="[{ 'is-loading': form.isSubmitting }, 'button', 'is-link']"
        >
          Submit
        </button>
      </div>
    </form>
  </div>
</template>

<script>
class Errors {
  constructor() {
    this.errors = {};
  }

  doHave(field) {
    return field in this.errors;
  }

  doHaveAny() {
    return Object.keys(this.errors).length > 0;
  }

  get(field) {
    return this.errors[field] ? this.errors[field] : null;
  }

  set(errors) {
    this.errors = errors;
  }

  clear(field) {
    if (field) {
      delete this.errors[field];
      return;
    }

    this.errors = {};
  }
}

class Form {
  constructor(data) {
    this.isSubmitting = false;

    this.originalData = data;

    for (const field in data) {
      this[field] = data[field];
    }

    this.errors = new Errors();
  }

  canSubmit() {
    return this.isValid() && !this.isSubmitting && !this.errors.doHaveAny();
  }

  submit() {
    return new Promise((resolve, reject) => {
      if (!this.validate()) {
        reject(this.errors);
        return;
      }

      this.isSubmitting = true;

      setTimeout(() => {
        this.isSubmitting = false;
        const data = this.data();
        this.onSuccess();
        resolve(data);
      }, 2000);
    });
  }

  isValid() {
    for (const field in this.originalData) {
      if (this[field] === "") {
        return false;
      }
    }

    return true;
  }

  validate() {
    let valid = true;
    let errors = {};

    for (const field in this.originalData) {
      if (this[field] === "") {
        errors[field] = `The ${field} is empty`;
        valid = false;
      }
    }

    this.errors.set(errors);
    return valid;
  }

  onSuccess() {
    alert("Success");
    this.reset();
  }

  reset() {
    this.isSubmitting = false;

    for (const field in this.originalData) {
      this[field] = null;
    }

    this.errors.clear();
  }

  data() {
    let data = {};

    for (const field in this.originalData) {
      data[field] = this[field];
    }

    return data;
  }
}

export default {
  name: "HelloWorld",
  data() {
    return {
      form: new Form({
        name: "",
        description: "",
      }),
    };
  },
  methods: {
    onSubmit() {
      this.form.submit().then(console.log).catch(console.log);
    },
  },
};
</script>

<style scoped>
</style>
