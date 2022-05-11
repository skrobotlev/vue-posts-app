<template>
  <form @submit.prevent>
    <h4>Create post</h4>
    <!-- V-BIND, V-FOR и т.д. НАЗЫВАЮТСЯ ДИРЕКТИВАМИ; @input - подписка на изменения, которую можно методом компонента, inputTitle(event) title=event.t.v
        или @input="title = $event.target.value" -->
    <!-- Директива  V-model для двустороннего связывания inputs, checkboxs, ul(li)  -->
    <!-- <input
      v-bind:value="post.title"
      @input="post.title = $event.target.value"
      class="input"
      type="text"
      placeholder="Name"
    /> -->
    <!-- <my-input v-model="post.title" type="text" placeholder="Title" /> -->
    <my-input v-model="post.title" type="text" placeholder="Title" />
    <my-input v-model="post.desc" type="text" placeholder="Desc" />
    <my-button
      @click="createPost"
      style="align-self: flex-end; margin-top: 15px"
      class="btn"
      >Create</my-button
    >
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: "",
        desc: "",
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit("create", this.post);
      this.post = {
        title: "",
        desc: "",
      };
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
