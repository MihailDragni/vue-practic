<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <my-button @click="showDialog">Создать пост</my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-dialog>

    <posts-list :posts="posts" @remove="removePost" />
  </div>
</template>

<script>
import PostForm from '@/components/PostForm.vue'
import PostsList from '@/components/PostsList.vue'
export default {
  components: { PostForm, PostsList },
  name: 'App',
  data() {
    return {
      posts: [
        {
          id: 1,
          title: 'JavaScript 1',
          body: 'Описание поста 1 ',
        },
        {
          id: 2,
          title: 'JavaScript 2',
          body: 'Описание поста 2',
        },
        {
          id: 3,
          title: 'JavaScript 3',
          body: 'Описание поста 3',
        },
        {
          id: 4,
          title: 'JavaScript 4',
          body: 'Описание поста 4',
        },
      ],
      dialogVisible: false,
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
    },
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>
