<script>
  export default {
    props: {
      post: {
        type: Object,
        required: true,
      }
    }
  }
</script>

<template>
  <div class="post">
    <div>
      <div><strong>Название: </strong>{{ post.title }}</div>
      <div><strong>Описание: </strong>{{ post.title }}</div>
    </div>
    <div class="post__btns">
      <my-button
        @click="$emit('remove', post)"
      >Удалить</my-button>
    </div>
  </div>
</template>

<style scoped>
.post {
  padding: 15px;
  border: 2px solid #12cbd0;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>