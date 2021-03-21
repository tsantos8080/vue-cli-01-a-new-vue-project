<template>
  <section>
    <li>
      <h2>{{ name }} {{ isFavorite ? "(Favorite)" : "" }}</h2>
      <button @click="toggleFavorite">Toggle favorite</button>
      <button @click="toggleDetails">Show details</button>
      <ul v-if="detailsAreVisible">
        <li><strong>Phone:</strong> {{ phoneNumber }}</li>
        <li><strong>Email:</strong> {{ emailAddress }}</li>
      </ul>
    </li>
  </section>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  emits: ["toggle-favorite"],
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit("toggle-favorite", this.id);
    },
  },
};
</script>