<template>
    <div class="Add-post">
      <div class="row mb-3 mt-2">
       <div class="col text-right"> 
        <button class="btn-primary" v-on:click="showform">Create a post</button>
       </div>
      </div>
      <div class="card mb-3" v-if="formdiv">
        <div class="card-body">
          <form @submit.prevent="addPost">
            <div class="form-group">
              <label>Post Title</label>
              <input type="text" v-model="title" name="title" class="form-control" placeholder="">
            </div>
            <div class="form-group">
              <label>Post Details</label>
              <textarea name="body" v-model="body" class="form-control" placeholder=""/>
            </div>
            <div class="row">
              <div class="com-6 mx-auto">
                <button class="btn btn-block btn-success">Create Post</button>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: "AddPost",
  data(){
    return{
      formdiv: false,
      title:"",
      body: ""
    };
  },
  methods:
  {
    showform(){
      this.formdiv = true;
    },
    addPost(){
      const newPost = {title: this.title, body: this.body};

      // Send up to Parent
      this.$emit("add-post",newPost);
      (this.title=""), (this.body=""),(this.formdiv = false);
    }
  }  
};
</script>


<style scoped>

</style>