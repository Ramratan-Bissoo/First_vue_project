<template>
    <div class="post-list">
      <div class="card mb-3"  v-for="post of post1" :key="post.id" @dblclick="$emit('del-post', post.id)">
        <div class="card-body">
          <h3><router-link :to="`/postdetails/${post.id}`">{{post.title}}</router-link></h3>
          <p>{{post.body}}</p>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: "PostList",
  props:["post1"]  
};
</script>


<style scoped>

</style>