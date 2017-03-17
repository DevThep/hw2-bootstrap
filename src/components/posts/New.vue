<template>
  <div class="container col-md-4 col-md-offset-4 new-post">
  	<h2>New Post</h2>
  	<label>Name</label>
  	<b-form-input v-model="post.name" type="text" placeholder=""></b-form-input>
  	<br>
  	<label>Content</label><br>
  	<textarea v-model="post.content" class="form-control" rows="4"></textarea>
  	<div class="sub-button">
  		<b-button size="md" variant="primary" @click="createPost">Save</b-button>
  	</div>
  </div>

</template>

<script>
import PostsApi from '../../api/posts.js'
import router from '../../router'

export default {
  name: 'new-post',
  data () {
    return {
      post: {
        name: '',
        content: ''
      }
    }
  },
  methods: {
    createPost () {
      PostsApi.createPost(this.post,
        function (_post) {
          router.push({ name: 'Posts.index' })
        }
      )
    }
  }
}
</script>

<style scoped>
	.new-post {
		padding-top: 30px;
	}

	h2 {
		padding-bottom: 10px;
		text-align: center;
	}

</style>
