<template>
  <div class="posts">
    <b-list-group-item v-for="post in posts" :key="post">
      <router-link class="col-lg-12" :to="{ name: 'Posts.show', params: {id: post.id } }">
        <iccs340-post :post='post'></iccs340-post>
      </router-link>
    </b-list-group-item>
  </div>
</template>

<script>
import PostsApi from '../../api/posts.js'

export default {
  name: 'posts',
  data () {
    return {
      posts: null,
      error: null
    }
  },
  beforeRouteEnter (to, from, _next) {
    PostsApi.getPosts(_posts => {
      _next(vm => {
        vm.posts = _posts
      })
    })
  },
  watch: {
    $route () {
      PostsApi.getPosts(_posts => {
        this.posts = _posts
      })
    }
  },
  components: {
    Iccs340Post: require('./Post')
  }
}
</script>

<style scoped>
  .posts {
    padding: 0 10px;
  }
</style>
