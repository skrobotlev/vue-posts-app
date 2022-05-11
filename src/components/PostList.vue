<template>
  <div class="post" :key="post.id" v-for="post in posts">
    <div><strong>Name:</strong>{{ post.title }}</div>
    <div><strong>About:</strong>{{ post.desc }}</div>
  </div>
</template>

<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.post {
  padding: 15px;
  margin-top: 15px;
  border: 2px solid teal;
}
</style>
