<script>
 import PostItem from '@/components/PostItem.vue'

 export default {
   components: { PostItem },
   props: {
     posts: {
       type: Array,
       required: true,
     }
   }
 }
</script>

<template>
  <div v-if="posts.length > 0">
    <h3>Список пользователей</h3>
    <post-item
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-else class="danger">
    Список постов пуст
  </h2>
</template>

<style scoped>
.danger {
  color: red;
  font-family: Arial, sans-serif;
}
</style>