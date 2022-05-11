<template>
  <select v-model="modelValue" @change="chengeOptions">
    <option disabled value="">Select from list</option>
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: "my-select",
  props: {
    modelValue: {
      type: String,
    },
    // для пустых массивов рекомендуется стрелочная функция?
    options: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    changeOption(event) {
      this.$$emit("update:modalValue", event.target.value);
    },
  },
};
</script>

<style></style>
