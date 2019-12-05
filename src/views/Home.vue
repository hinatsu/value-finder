<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <ValueFinder msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import ValueFinder from '@/components/ValueFinder.vue';

export default {
  name: 'home',
  components: {
    ValueFinder
  }
};
</script>
