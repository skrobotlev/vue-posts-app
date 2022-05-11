<template>
  <form @submit.prevent>
    <h4>Create post</h4>
    <!-- V-BIND, V-FOR и т.д. НАЗЫВАЮТСЯ ДИРЕКТИВАМИ; @input - подписка на изменения, которую можно методом компонента, inputTitle(event) title=event.t.v
        или @input="title = $event.target.value" -->
    <input
      v-bind:value="post.title"
      @input="post.title = $event.target.value"
      class="input"
      type="text"
      placeholder="Name"
    />
    <!-- Директива  V-model для двустороннего связывания inputs, checkboxs, ul(li)  -->
    <!-- <input
      v-bind:value="post.title"
      @input="post.title = $event.target.value"
      class="input"
      type="text"
      placeholder="Name"
    /> -->
    <input
      v-bind:value="post.desc"
      @input="post.desc = $event.target.value"
      class="input"
      type="text"
      placeholder="Desc"
    />
    <button class="btn">Create</button>
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
};
</script>

<style scoped>
.input {
  width: 100%;
  border: 2px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
form {
  display: flex;
  flex-direction: column;
}
.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background-color: none;
  color: teal;
  border: 1px solid teal;
}
</style>
