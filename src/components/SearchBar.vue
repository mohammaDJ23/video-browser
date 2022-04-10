<template>
  <div>
    <input @input="onInput" />
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onInput(event) {
      // emit the function form here to parent
      // to passing value from here to parent state by callback event system

      this.$emit('termChange', event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  width: 75%;
}

div {
  text-align: center;
  margin: 20px;
}
</style>
