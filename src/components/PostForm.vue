<script>

  import MyInput from '@/components/UI/MyInput.vue'
  import MyButton from '@/components/UI/MyButton.vue'

  export default {
    components: { MyButton, MyInput },
    data() {
      return {
        post: {
          title: '',
          body: ''
        }
      }
    },
    methods: {
      createPost() {
        this.post.id = Date.now();
        this.$emit('create', this.post, 'second', '3d')
        this.post = {
          title: '',
          body: ''
        }
      }
    }
  }
</script>

<template>
    <form @submit.prevent>
      <h3>Создание поста</h3>
      <my-input
        v-model="post.title"
        type="text"
        placeholder="Название"
      />
      <my-input
        v-model="post.body"
        type="text"
        placeholder="Описание"
      />

      <my-button
        class="form__btn"
        @click="createPost"
      >Создать</my-button>
    </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}

.form__btn {
  margin-top: 15px;
  align-self: flex-end;
}
</style>