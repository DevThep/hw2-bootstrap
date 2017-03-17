<template>
  <div class="post">
      <b-list-group-item class="container">
      <iccs340-post :post='post' class="a-post col-lg-12"></iccs340-post>
      </b-list-group-item>
      <iccs340-new-comment :post='post'></iccs340-new-comment>
      <h5>Comments</h5>
      <b-list-group-item v-for="comment in comments" :key="comment">
        <iccs340-comment :comment='comment' class="col-lg-10"></iccs340-comment>
      </b-list-group-item>
  </div>
</template>

<script>
import PostsApi from '../../api/posts.js'
import CommentsApi from '../../api/comments.js'

export default {
  name: 'post',
  components: {
    Iccs340Post: require('./Post'),
    Iccs340Comment: require('../comments/Comment'),
    Iccs340NewComment: require('../comments/New')
  },
  data () {
    return {
      post: {},
      comments: [],
      error: null
    }
  },
  created () {
    // fetch the data when the view is created and the data is
    // already being observed
    this.fetchData()
  },
  watch: {
    // call again the method if the route changes
    '$route': 'fetchData'
  },
  methods: {
    fetchData () {
      PostsApi.getPost(this.$route.params.id, _post => {
        this.post = _post
        CommentsApi.getComments(_post.id, _comments => {
          this.comments = _comments
        })
      })
    }
  }
}
</script>

<style scoped>
  .a-post {
    margin: 0 auto;
  }
</style>
