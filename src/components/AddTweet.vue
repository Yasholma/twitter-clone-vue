<template>
  <div class="add-tweet">
    <form class="add-tweet__form" @submit.prevent="submitTweet">
      <div class="field">
        <label for="body" class="add-tweet__form__label">
          Tweet (max: 180)
        </label>
        <textarea
          name="body"
          id="body"
          class="add-tweet__form__body"
          rows="3"
          v-model="body"
        ></textarea>
      </div>
      <div class="field">
        <label for="type" class="add-tweet__form__label"> Tweet Type </label>
        <select
          name="type"
          v-model="selectedType"
          id="type"
          class="add-tweet__form__type"
        >
          <option v-for="type in types" :key="type.name" :value="type.value">
            {{ type.name }}
          </option>
        </select>
      </div>

      <button>Tweet</button>
    </form>
  </div>
</template>

<script>
export default {
  data: () => ({
    body: "",
    selectedType: "instant",
    types: [
      { name: "Draft", value: "draft" },
      { name: "Instant", value: "instant" },
    ],
  }),

  methods: {
    submitTweet() {
      if (this.body && this.selectedType !== "draft") {
        this.$emit("new-tweet", this.body);
        this.body = "";
      }
    },
  },
};
</script>

<style>
.add-tweet {
  width: 100%;
  margin-top: 2.5rem;
}

.add-tweet__form,
.add-tweet__form__body {
  width: 100%;
  margin-bottom: 0.5rem;
}

.add-tweet__form__label {
  font-size: 1.2rem;
  font-weight: bold;
  display: block;
}

.add-tweet__form__body {
  border: 1px solid #ccc;
  margin: 1rem 0;
  padding: 0.5rem;
  padding-right: 0;
  box-sizing: border-box;
}

.add-tweet__form__type {
  margin: 1rem 0;
}
</style>