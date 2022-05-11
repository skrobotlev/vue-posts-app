<template>
  <div v-show="posts.length > 0">
    <!-- ЧТОБЫ ЭЛЕМЕНТ H2 БЫЛ В ДОМ ДЕРЕВЕ ВСЕГДА И ПРОСТО СКРЫТ,V-SHOW; ИЛИ ПО УСЛОВИЮ IF ELSE ВСТРАИВАТЬСЯ В ДЕРЕВО -->
    <!-- <div v-if="posts.length > 0"> -->
    <h3>Users list</h3>
    <post-item
      :post="post"
      :key="post.desc"
      v-for="post in posts"
      @remove="$emit('remove', post)"
    />
  </div>
  <!-- <h2 v-else style="color: red">Empty list</h2> -->
  <h2 v-show="posts.length === 0" style="color: red">Empty list</h2>
</template>

<script>
import PostItem from "./PostItem.vue";
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped></style>
