<template>
  <!-- <input :value="modelValue" @input="updateInput" class="input" type="text" /> -->
  <input :value="modelValue" @input="updateInput" class="input" type="text" />
</template>

<script>
export default {
  name: "my-input",
  props: {
    modelValue: [String, Number],
    // value: [String, Number],
    // myvalue: [String],
  },
  methods: {
    updateInput(event) {
      this.$emit("update:modelValue", event.target.value);
      //   this.$emit("update:value", event.target.value);
      //   this.$emit("update:myvalue", event.target.value);
    },
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
</style>
