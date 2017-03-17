<template>
  <div class="comment">
    <b-list-group-item>
      <div class="list-text-container">
        <i class="material-icons blue600">account_circle</i>
        <span><b>{{ comment.user.email }}</b></span>
        <hr />
        <span>{{ comment.content }}</span>
      </div>
    </b-list-group-item>
  </div>
</template>

<script>

export default {
  name: 'comment',
  props: {
    comment: {
      type: Object,
      required: false,
      default: {}
    }
  }
}
</script>

<style scoped>
  .list-text-container {
    padding-left: 30px;
  }
  .comment {
    margin: 0 auto;
  }
  .material-icons.blue600 { 
    color: #4169E1;
  }
</style>
