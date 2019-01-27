<template>
  <div class="heroImage" />
</template>

<script>
export default {
  name: 'HeroImage',
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.heroImage {
  position: fixed;
  top: 0;
  z-index: -1;
  width: 100%;
  height: 100vh;
  background-image: url("../assets/background.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 50% bottom;
}
</style>
