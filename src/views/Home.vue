<template>
  <div class="home">
   <AddPost v-on:add-post="addPost"/>
   <PostList v-on:del-post="deletepost" :post1="posts"/>
   
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
import AddPost from '@/views/AddPost.vue';
import PostList from '@/views/PostList.vue';

export default {
  name: "home",
  components: {
   AddPost,
   PostList,
   
  },
  data(){
    return{
      posts:[],
      error:[],
      resp:[]
    };
  },
  methods: {
    addPost(newPost){
      const {title, body} = newPost;
      axios.post("https://jsonplaceholder.typicode.com/posts",{title,body})
      .then(res => {this.posts = [...this.posts, res.data]})
      .catch(err => {console.log(err)});
    },
    deletepost(id){
      axios.delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
      .then(res => {
        this.posts = this.posts.filter(post => post.id !== id)
        this.resp = res
      })
      .catch(err =>{console.log(err)});
    }
  },
  created(){
    axios.get(`https://jsonplaceholder.typicode.com/posts?_limit=5`)
    .then(resp=>{
      this.posts = resp.data;
      console.log(this.posts);
    })
    .catch(e =>{
      this.error.push(e);
    })
  }
}
</script>
