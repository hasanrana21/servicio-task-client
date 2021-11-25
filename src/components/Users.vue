<template>
  <div v-for="(user, index) in allUsers" :key="index" class="userInfo">
    <h2>{{ user.title }}</h2>
    <p>{{ user.description }}</p>
    <p>{{user._id}}</p>
    <div>
      <button>Edit</button>
      <button @click="deleteUser(user._id)">Delete</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Users",
  data() {
    return {
      allUsers: [],
    };
  },

  mounted() {
    axios
      .get("http://localhost:5050/getUsers")
      .then((res) => {
        console.log(res.data);
        this.allUsers = res.data;
      })
      .catch((err) => console.log(err));
  },

  methods: {
    deleteUser(id) {
    axios.delete('')
      console.log(id)
    },
  },
};
</script>

<style scoped>
.userInfo button {
  margin: 0 15px;
}
</style>
