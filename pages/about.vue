<template>
  <div class="container">
    <p>Hi from {{ name }}</p>
    <p>
      It should take 2 seconds for the route to change after you
      <span class="link" @click="goToFinal">click here</span>
    </p>
  </div>
</template>

<script>
export default {
  layout: 'dark',
  asyncData() {
    // this can delay rendering.
    return new Promise((resolve) => {
      setTimeout(function () {
        resolve({
          name: process.static ? 'static' : (process.server ? 'server' : 'client'),
        });
      }, 500);
    });
  },
  head: {
    title: 'About - Inclusive Examples',
  },
  methods: {
    goToFinal() {
      this.$nuxt.$loading.start()

      setTimeout(() => {
        this.$router.push('/final');
      }, 2000);
    },
  },
};
</script>

<style scoped>
.link {
  cursor: pointer;
  text-decoration: underline;
}
</style>
