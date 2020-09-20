<template>
  <div>
    <input @keypress.enter="onInput" type="text" class="form-control" placeholder="Search" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput: function (event) {
      this.$emit("termChange", event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  width: 75%;
  text-align: center;
}

div {
  text-align: center;
  margin: 20px;
}
</style>
