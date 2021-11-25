<template>
  <div>
      <h1 :style="{textAlign: 'center', fontSize: '43px'}">Add User</h1>
    <div class="form-wrapper">
      <form action="#" @submit.prevent="handleSubmit()">
        <label for="title">Title</label> <br />
        <input
          type="text"
          name="title"
          placeholder="Write a user name"
          id="title"
          v-model="user.title"
        />
        <br /><br />

        <label for="description">Description</label> <br />
        <!-- <input
          type="text"
          name="description"
          id="description"
          v-model="user.description"
        /> -->
        <textarea
          type="text"
          name="description"
          id="description"
          v-model="user.description"
          cols="10"
          rows="3"
          placeholder="Description"
        >
        </textarea>
        <br /><br />

        <button type="submit" class="submit-btn">Submit</button>
      </form>
    </div>
    <div class="userDetails">
      <div v-for="(user, index) in allUsers" :key="index" class="userInfo">
        <h2>{{ user.title }}</h2>
        <p>{{ user.description }}</p>
        <p>{{ user._id }}</p>
        <div>
          <button @click="editUser(user._id)">Edit</button>
          <button @click="deleteUser(user._id)">Delete</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Users",
  data() {
    return {
      user: {
        title: "",
        description: "",
      },
      allUsers: [],
      //   editInput: false,
      //   editTitle: '',
      //   editDescription: '',
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
    handleSubmit() {
      axios
        .post("http://localhost:5050/newUser", this.user)
        .then((res) => console.log(res))
        .catch((err) => console.log(err));
      console.log("submited", this.user);
    },
    deleteUser(id) {
      axios.delete("http://localhost:5050/delete/" + id).then((res) => {
        console.log(res);
      });
      console.log("delete data", id);
    },

    // editUser(id) {
    //   axios
    //   .patch('http://localhost:5050/updateUser/' + id, {
    //          title : this.editTitle,
    //          description : this.editDescription
    //   })
    // },
  },
};
</script>

<style scoped>
.userInfo button {
  margin: 0 15px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
.form-wrapper {
  width: 50%;
  margin: 0 auto;
  padding-bottom: 15px;
}
.form-wrapper input,
textarea {
  padding: 10px 10px;
  width: 100%;
  font-size: 21px;
  margin-top: 7px;
}
.userDetails{
    display: flex;
    flex-wrap: wrap;
    padding: 0 25px;
    margin: 1% 15%;
}
.userInfo {
  width: 450px;
  margin: 10px 15px;
  padding: 35px;
  border: 2px solid green;
  border-radius: 20px;
}
.submit-btn {
  padding: 5px 30px;
  font-size: 21px;
  cursor: pointer;
}
label {
  font-size: 21px;
}
</style>
