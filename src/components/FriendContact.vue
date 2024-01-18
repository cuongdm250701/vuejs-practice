<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? "Favorite" : "" }}</h2>
    <button @click="onShowDetail">Show Details</button>
    <button @click="toggleFavorite(id)">Toggle Favorite</button>
    <ul v-if="showDetail">
      <li>{{ phoneNumber }}</li>
      <li>{{ emailAddress }}</li>
    </ul>
  </li>
</template>
<script>
export default {
  props: ["name", "phoneNumber", "emailAddress", "isFavorite", "id"],
  emits: {
    "toggle-favorite": function (id) {
      if (id) {
        return true;
      } else {
        console.error("id is missing");
      }
    },
  },
  data: function () {
    return {
      showDetail: false,
    };
  },
  methods: {
    onShowDetail: function () {
      this.showDetail = !this.showDetail;
    },
    toggleFavorite: function () {
      this.$emit("toggle-favorite", this.id);
    },
  },
};
</script>
