<template>
  <form>
    <input type="search" @input="search" :value="searchTerm" placeholder="Filter items" />
  </form>
</template>

<script>
export default {
  props: ['searchTerm'],
  emits: ['search'],
  methods: {
    search(event) {
      this.$emit('search', event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  font: inherit;
  width: 100%;
  display: block;
  padding: 0.15rem;
  border: 1px solid #EA7317;
}

input:focus {
  outline: none;
  border-color: #EA7317;
  background-color: #FEC601;
}
</style>