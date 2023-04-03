<template>
  <NotesComponents />
  <div class=""></div>
</template>

<script>
import NotesComponents from './components/NotesComponents.vue'

export default {
  name: 'App',
  components: {
    NotesComponents

  }
}

</script>

<style>
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';

.title {
  text-transform: uppercase;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f2eee3;
  margin-top: 60px;
}

@media screen and (min-width: 1024px) {
  .title {
    color: #f2eee3;
  }
}
</style>
