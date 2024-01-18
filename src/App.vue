<template>
  <section>
    <h2>My Friends</h2>
    <ul>
      <friend-contact
        v-for="friend in friends"
        :key="friend.id"
        :name="friend.name"
        :phone-number="friend.phone"
        :email-address="friend.email"
        :is-favorite="friend.isFavorite"
        :id="friend.id"
        @toggle-favorite="toggleFavorite"
      ></friend-contact>
    </ul>
  </section>
</template>
<script>
export default {
  data: function () {
    return {
      friends: [
        {
          id: "1",
          name: "Manuel Lorenz",
          phone: "010202012",
          email: "manuel@gmail.com",
          isFavorite: true,
        },
        {
          id: "2",
          name: "July Lorenz",
          phone: "020320101",
          email: "july@gmail.com",
          isFavorite: false,
        },
      ],
    };
  },

  methods: {
    toggleFavorite: function (id) {
      const identified = this.friends.find((item) => item.id === id);
      identified.isFavorite = !identified.isFavorite;
    },
  },
};
</script>
