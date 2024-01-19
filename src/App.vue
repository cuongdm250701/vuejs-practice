<template>
  <section>
    <add-contract @add-contract="addContract"></add-contract>
  </section>
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
        @delete-contract="deleteContract"
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
    addContract: function (newContract) {
      const newContracter = {
        ...newContract,
        id: this.friends.length + 1,
        isFavorite: false,
      };
      this.friends.push(newContracter);
    },
    deleteContract: function (id) {
      this.friends = this.friends.filter((item) => item.id !== id);
    },
  },
};
</script>
