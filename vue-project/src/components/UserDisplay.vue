<template>
  <div>
    <h1>User Profile</h1>
    <p>Name: {{ user.name }}</p>
    <p>Age: {{ user.age }}</p>
    <p>Email: {{ user.email }}</p>
    <p>Birth Year: {{ birthYear }}</p>
    <ul>
      <li v-for="hobby in user.hobbies" :key="hobby">{{ hobby }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    user: Object,
  },
  computed: {
    birthYear() {
      return new Date().getFullYear() - this.user.age;
    },
  },
  watch: {
    'user.age': function(newAge) {
      if (newAge > 60) {
        alert("You're getting old!");
      }
    },
  },
};
</script>