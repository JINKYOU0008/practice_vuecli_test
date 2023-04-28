<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <button class="btn btn-primary" type="submit">{{ name }}</button>
  <router-view/>
</template>

<script>
export default {
  data() {
    return {
      name: process.env.VUE_APP_NAME,
    };
  },
};
</script>

<style lang="scss">
@import 'bootstrap';
</style>
