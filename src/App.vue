<template>
  <div class="app">
    <!-- v-bind:posts || :posts короткая запись -->
    <h1>Posts page</h1>
    <my-button @click="showDialog">Create post</my-button>
    <my-dialog v-model:show="dialogVisible">
      <PostForm @create="createPost" />
    </my-dialog>
    <PostList @remove="removePost" :posts="posts" />
  </div>
</template>

<script>
import PostList from "./components/PostList";
import PostForm from "@/components/PostForm";
export default {
  components: { PostList, PostForm },
  data() {
    //   ДАННЫЕ ВНУТРИ ДАТА ТИПА posts НАЗЫВАЮТСЯ МОДЕЛИ, А ЭТО Я СЧИТАЮ АНАЛОГ ЛОКАЛЬНОГО СТЕЙТА
    return {
      posts: [
        { id: 1, title: "JS spa", desc: `Opisanie posta 1` },
        { id: 2, title: "JS spa", desc: "Opisanie posta 2" },
        { id: 3, title: "JS spa", desc: "Opisanie posta 3" },
        { id: 4, title: "JS spa", desc: "Opisanie posta 4" },
      ],
      dialogVisible: false,
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    // inputTitle(event) {
    //   console.log(event);
    //   this.title = event.target.value;
    // },
  },
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
</style>
