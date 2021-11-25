<template>
  <div class="hello">
    <form action="" @submit.prevent="handleSubmit">
      <label for="title">Title</label> <br>
      <input type="text" name="title" id="title" v-model="title" /> <br><br>

      <label for="description">Description</label> <br>
      <input type="text" name="description" id="description" v-model="description" /> <br><br>

      <input type="submit" value="Submit">
    </form>

    <div>
      <ul>
        <li v-for="(list, index) in lists" :key="index">
          <p>{{list.title}}</p>
          <p> {{ list.description}}</p>
          <button @click="editList(index)" :style="{margin: '0px 10px'}">Edit</button>
          <button @click="deleteList">Delete</button>
          <p> {{index}} </p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      title: '',
      description: '',
      lists: [
        {
          title: 'apple',
          description: 'lorem1asdkfjalskdjfadfkajsdf'
        }
      ]
    }
  },

  methods:{
    handleSubmit(){
      this.lists.push({
        title: this.title,
        description: this.description,
      })
    },

    deleteList(){
      this.lists.pop();
    },

    editList(index){
      // this.lists[index === ]
      console.log(this.lists[index].title)
      
      this.lists[index].title

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
