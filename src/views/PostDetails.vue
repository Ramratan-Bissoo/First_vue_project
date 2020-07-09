<template>
    <div class="post-details">
      <div class="card mb-3">
        <div class="card-body">
          <h3>{{post.title}}</h3>
          <p>{{post.body}}</p>
        </div>
      </div>
      <PostComments />
    </div>
</template>

<script>
import axios from 'axios';

import PostComments from '@/views/PostComments.vue';
export default {
  name: "PostDetails",
  components: {
    PostComments
  },
  data(){
    return{
      id: this.$route.params.id,
      post:[]
    };
  },
  created()
  {
    axios.get(`https://jsonplaceholder.typicode.com/posts/${this.id}`)
    .then(res=>{
      this.post = res.data;
    })
    .catch(e =>{
      console.log(e);
    })
  }  
};
</script>


<style scoped>

</style>