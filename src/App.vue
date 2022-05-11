<template>
  <div class="app">
    <!-- v-bind:posts || :posts короткая запись -->
    <PostForm />
    <PostList :posts="posts" />

    <!-- <div></div> -->
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
        { id: 1, title: "JS spa", desc: `Opisanie posta ${this.id}` },
        { id: 2, title: "JS spa", desc: "Opisanie posta" },
        { id: 3, title: "JS spa", desc: "Opisanie posta" },
        { id: 4, title: "JS spa", desc: "Opisanie posta" },
      ],
      title: "",
      desc: "",
    };
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        desc: this.desc,
        title: this.title,
      };
      this.posts.push(newPost);
      this.title = "";
      this.desc = "";
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
