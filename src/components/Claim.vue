<template>
  <div class="claimWrapper">
    <img class="claim" src="../assets/logo_big.png" />
    <p class="subclaim">
      Begin your journey through our amazing galaxy, and discover places you
      never even heard of.
    </p>
    <p class="subclaim">Type anything space-related to start.</p>
  </div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.claimWrapper {
  display: flex;
  text-align: center;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: #fff;

  img.claim {
    max-width: 80%;
    margin: 0 0 20px 0;
  }

  .subclaim {
    margin: 20px 0 0 0;
    font-size: 13px;
    font-weight: 400;

    @media (min-width: 768px) {
      width: 500px;
      font-size: 17px;
      line-height: 1;
      letter-spacing: 1px;
    }
  }
}
</style>
