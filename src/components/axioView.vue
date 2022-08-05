<template>
  <div id="app">
    <table class="table">
      <thead>
        <th>Id</th>
        <th>Title</th>
        <th>Body</th>
      </thead>
      <tbody>
        <tr v-for=" (post,index) in postData" :key="index">
          <td>{{post.id}}</td>
          <td>{{post.title}}</td>
          <td>{{post.body}}</td>
          <td>
            <b-button variant="info" @click="viewstatus(post.id)" >Show</b-button>
            <b-button variant="warning" @click="editstatus(post.id)" >Edit</b-button>
            <b-button variant="danger" @click="deletestatus(post.id)" >Delete</b-button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      postData: null,
    };
  },
  mounted() { this.getposts()},
  methods: {
    getposts() {
      axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then((response) => {
            this.postData = response.data;
            console.log(this.postData);
        }
            
        );
    },
    viewstatus(id) {
        console.log(id);
    },
    editstatus(id) {
        console.log(id);
    },
    deletestatus(id) {
        console.log(id);

        axios.delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
             .then(response => {
                 console.log(response);
             })
             .catch(function (error) {
                console.log(error.response)
             })
    }
  },
};
</script>