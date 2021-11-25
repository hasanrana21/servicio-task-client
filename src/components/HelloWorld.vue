<template>
  <div class="hello">
    <form action="#" @submit.prevent="handleSubmit">
      <label for="title">Title</label> <br />
      <input type="text" name="title" id="title" v-model="user.title" /> <br /><br />

      <label for="description">Description</label> <br />
      <input
        type="text"
        name="description"
        id="description"
        v-model="user.description"
      />
      <br /><br />

      <input type="submit" value="Submit" />
    </form>

    <div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      user: {
        title: "",
        description: "",
      },
    };
  },
  methods: {
    handleSubmit() {
      axios
      .post("http://localhost:5050/newUser", this.user)
      .then((res) => console.log(res))
      .catch((err) => console.log(err));
      console.log("submited", this.user);
    },

    // deleteList() {
    //   this.lists.pop();
    // },

    // editList(index) {
    //   console.log(this.lists[index].title);

    //   this.lists[index].title;
    // },
  },
};
</script>

<style scoped>
.hello{
  text-align: center;
}
</style>
