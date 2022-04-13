<template>
  <Main msg="Welcome to Your Vue.js + TypeScript App"/>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Main from './components/main.vue';

@Component({
  components: {
    Main,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
body{
  margin: 0;
  padding: 0;
}
</style>
