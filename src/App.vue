<script>
  import PostList from '@/components/PostList.vue'
  import PostForm from '@/components/PostForm.vue'
  import MyDialog from '@/components/UI/MyDialog.vue'
  import MyButton from '@/components/UI/MyButton.vue'
  import axios from 'axios'
  import MySelect from '@/components/UI/MySelect.vue'

  export default {
    components: {
      MySelect,
      MyButton,
      MyDialog,
      PostList,
      PostForm
    },
    data() {
      return {
        posts: [],
        dialogVisible: false,
        isPostsLoading: false,
        selectedSort: '',
        sortOptions: [
          {value: 'title', name: 'По названию'},
          {value: 'body', name: 'По описанию'},
        ]
      }
    },
    methods: {
      createPost(post) {
        this.posts.push(post);
        this.dialogVisible = false;
      },
      removePost(post) {
        this.posts = this.posts.filter(p => p.id !== post.id)
      },
      showDialog() {
        this.dialogVisible = true;
      },
      async fetchPost() {
        try {
          this.isPostsLoading = true;
            const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
            this.posts = response.data;
        } catch (e) {
          alert('Ошибка');
        } finally {
          this.isPostsLoading = false;
        }
      }
    },
    mounted() {
      this.fetchPost();
    }
  }
</script>

<template>
  <div class="app">
    <h1 class="main-title">Страница с постами</h1>
    <div class="app__btns">
      <my-button
        @click="showDialog"
      >Создать пост
      </my-button>
      <my-select
        v-model="selectedSort"
        :options="sortOptions"
      />
    </div>
    <my-dialog v-model:show="dialogVisible">
      <post-form
        @create="createPost"
      />
    </my-dialog>
    <post-list
      :posts="posts"
      @remove="removePost"
      v-if="!isPostsLoading"
    />
    <div v-else>Идёт загрузка...</div>
  </div>
</template>

<style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .app {
    padding: 20px;
  }

  .main-title {
    margin: 15px 0;
  }

  .app__btns {
    margin: 15px 0;
    display: flex;
    justify-content: space-between;
  }
</style>