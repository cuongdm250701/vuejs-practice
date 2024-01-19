<template>
  <h1>Add contract</h1>
  <form @submit.prevent="addContract">
    <div>
      <label>Name</label>
      <input type="text" v-model="name" />
    </div>
    <div>
      <label>Phone</label>
      <input type="phone" v-model="phone" />
    </div>
    <div>
      <label>Email</label>
      <input type="text" v-model="email" />
    </div>
    <button>Add</button>
  </form>
</template>

<script>
export default {
  data: function () {
    return {
      name: "",
      phone: "",
      email: "",
    };
  },
  methods: {
    addContract: function () {
      this.$emit("add-contract", {
        name: this.name,
        phone: this.phone,
        email: this.email,
      });
    },
  },
};
</script>
