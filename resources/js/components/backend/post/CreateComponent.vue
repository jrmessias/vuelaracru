<template>
  <div>
    <h1>Create A Post</h1>
    <form @submit.prevent="addPost">
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label>Post Title:</label>
            <input  v-validate="post.title" data-rules="required" type="text" class="form-control" name="title" v-model="post.title">
            <small v-if="errors.has('post.title')">{{ errors.first('post.title') }}</small>
          </div>
        </div>
        </div>
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label>Post Body:</label>
              <textarea v-validate="post.body" data-rules="required" name="body" class="form-control" v-model="post.body" rows="5"></textarea>
              <small v-if="errors.has('post.body')">{{ errors.first('post.body') }}</small>
            </div>
          </div>
        </div><br />
        <div class="form-group">
          <button class="btn btn-primary">Create</button>
        </div>
    </form>
  </div>
</template>

  <script>
    export default {
        data(){
        return {
          post:{}
        }
    },
    methods: {
      addPost(){
        console.log(this.post);
        let uri = 'http://www.vuelaracrud.localhost.com/api/post/create';
        this.axios.post(uri, this.post).then((response) => {
          this.$router.push({name: 'posts'});
        });
      }
    }
  }
</script>
