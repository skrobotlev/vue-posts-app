<template>
  <div class="app">
    <!-- v-bind:posts || :posts короткая запись -->
    <h1>Posts page</h1>
    <div class="app__btns">
      <my-button @click="showDialog">Create post</my-button>
      <my-select v-model="selectedSort" :options="sortOptions" />
    </div>
    <my-dialog v-model:show="dialogVisible">
      <PostForm @create="createPost" />
    </my-dialog>
    <PostList v-if="!isPostsLoading" @remove="removePost" :posts="posts" />
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostList from "./components/PostList";
import PostForm from "@/components/PostForm";
import axios from "axios";
export default {
  components: { PostList, PostForm },
  data() {
    //   ДАННЫЕ ВНУТРИ ДАТА ТИПА posts НАЗЫВАЮТСЯ МОДЕЛИ, А ЭТО Я СЧИТАЮ АНАЛОГ ЛОКАЛЬНОГО СТЕЙТА
    return {
      posts: [],
      dialogVisible: false,
      modificatorValue: "",
      isPostsLoading: false,
      selectedSort: "",
      sortOptions: [
        { value: "title", name: "On name" },
        { value: "body", name: "On desc" },
      ],
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
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        const response = await axios.get(
          "https://jsonplaceholder.typicode.com/posts?_limit=10"
        );
        //   console.log(response);
        this.posts = response.data;
      } catch (error) {
        console.log(error);
      } finally {
        this.isPostsLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPosts();
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
.app__btns {
  margin: 15px 0;
  display: flex;
  justify-content: space-between;
}
</style>
