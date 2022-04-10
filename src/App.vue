<template>
  <div><SearchBar @termChange="onTermChange" /></div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';

export default {
  name: 'App',
  components: {
    SearchBar,
  },
  methods: {
    onTermChange(value) {
      console.log(value);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
