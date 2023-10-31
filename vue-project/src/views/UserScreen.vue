<template>
  <div>
    <user-display :user="user" />
    <user-form :user="user" @update-user="updateUser" />
  </div>
</template>

<script>
import UserDisplay from "../components/UserDisplay.vue";
import UserForm from "../components/UserForm.vue";

export default {
  components: {
    UserDisplay,
    UserForm,
  },
  data() {
    return {
      user: {
        name: "John Doe",
        age: 30,
        email: "johndoe@example.com",
        hobbies: ["Reading", "Gaming", "Traveling"],
      },
    };
  },
  methods: {
    updateUser(updatedUser) {
      this.user = { ...updatedUser };
    },
  },
};
</script>