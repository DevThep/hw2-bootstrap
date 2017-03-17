<template>
  <div class="new-post">
      <b-list-group-item class="container">
        <i class="material-icons">folder</i>
          <label>Add Comment</label>
            <textarea v-model="comment.content" class="form-control" rows="3"></textarea>
      </b-list-group-item>
      <b-list-group-item class="container">
        <b-button @click="createComment" class="bt">Save</b-button>
      </b-list-group-item>
  </div>
</template>

<script>
import CommentsApi from '../../api/comments.js'
import router from '../../router'

export default {
  name: 'new-comment',
  data () {
    return {
      comment: {
        content: ''
      }
    }
  },
  props: {
    post: {
      type: Object,
      required: false,
      default: {}
    }
  },
  methods: {
    createComment () {
      var postId = this.post.id
      var content = this.comment.content
      this.comment.content = ''
      CommentsApi.createComment(postId, content,
        function (_comment) {
          console.log(_comment)
          router.push({ name: 'Posts.show', params: { post_id: postId }, query: { t: new Date() } })
        }
      )
    }
  }
}
</script>

<style scoped>
  .bt {
    margin: 0 auto;
  }
</style>
