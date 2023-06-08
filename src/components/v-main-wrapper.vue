<template>
  <div class="v-main-wrapper">
    <p>{{ title }}</p>
  </div>
</template>

<script>
export default {
  name: 'v-main-wrapper',
  data() {
    return {
      title: 'Main wrapper',
    };
  },
};
</script>

<style scoped>
.v-main-wrapper {
  max-width: 900px;
  margin: 0 auto;
}
</style>
