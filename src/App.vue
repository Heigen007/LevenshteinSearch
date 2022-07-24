<template>
  <MainPage/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import MainPage from './components/MainPage.vue';

@Options({
  components: {
    MainPage,
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body{
  padding: 0;
  margin: 0;
}
</style>
