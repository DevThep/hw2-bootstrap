<template>
  <div class="post">
    <i class="material-icons orange600 md-42">account_circle</i>
    <div class="name col-md-6">
      <div class="block">
        <b>{{ post.name }}</b>
      </div>
    </div>
    <b-list-group-item>
        <p>{{ post.content }}</p>
    </b-list-group-item>
  </div>
</template>

<script>
export default {
  name: 'post',
  props: {
    post: {
      type: Object,
      required: false,
      default: {}
    }
  }
}

</script>
<style scoped>
  .name {
    padding: 8px;
    position: relative;
    display: inline-block;
  }
  .block {
    position: absolute;
    top: -15px;
    left: 0px;
  }
  .material-icons.orange600 { 
    color: #FB8C00;
  }
  .material-icons.md-42 { font-size: 42px; }
</style>
