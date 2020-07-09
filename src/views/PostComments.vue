<template>
  <div class="Post-comments">
     <div class="card bg-dark mb-2" v-for="comment of comments" :key="comment.id">
        <div class="row no-gutters">
        <div class="col-md-2">
          <img src="@/assets/4.png" class="card-img" alt="...">
        </div>
      <div class="col-md-10">
        <div class="card-body">
        <h5 class="card-title">{{comment.name}}</h5>
        <p class="card-text">{{comment.body}}</p>
        <p class="card-text"><small class="text-muted">{{comment.email}}</small></p>
      </div>
     </div>
     </div>
   </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "PostComments",
  data(){
    return {
      comments:[],
      id : this.$route.params.id
    };
  },
  created(){
   axios.get(`https://jsonplaceholder.typicode.com/comments?postId=${this.id}`)
   .then(res=>{
     this.comments = res.data;
   })
   .catch(e =>{
     console.log(e);
   })
  }  
};
</script>


<style scoped>

</style>