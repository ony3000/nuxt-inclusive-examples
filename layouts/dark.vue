<template>
  <div class="dark">
    <nuxt/>
    <visits/>
  </div>
</template>

<script>
import Visits from '~/components/visits'

export default {
  components: {
    Visits,
  },
};
</script>

<style>
body {
  overflow: hidden;
}
.dark {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  min-height: 100%;
  background: #222;
  color: white;
  padding: 10px;
}
.dark a {
  color: white;
}
</style>
