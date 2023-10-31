<template>
  <div>
    <form @submit.prevent="saveProfile">
      <label for="name">Name:</label>
      <input v-model="updatedUser.name" type="text" id="name">

      <label for="age">Age:</label>
      <input v-model="updatedUser.age" type="number" id="age">

      <label for="email">Email:</label>
      <input v-model="updatedUser.email" type="email" id="email">

      <button type="submit">Save Profile</button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    user: Object, // Pass the user object as a prop
  },
  data() {
    return {
      updatedUser: {
        name: "",
        age: null,
        email: "",
      },
    };
  },
  methods: {
    saveProfile() {
      this.$emit("update-user", this.updatedUser);
      this.updatedUser = {
        name: "",
        age: null,
        email: "",
      };
    },
  },
};
</script>