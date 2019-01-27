<template>
  <div class="aboutWrapper page">
    <div class="nav">
      <router-link to="/"
        ><img class="logo" src="../assets/logo_small.png"
      /></router-link>
      <router-link to="/about"
        ><img class="about" src="../assets/about.png"
      /></router-link>
    </div>

    <h1 class="ml12">
      <span class="letter">A</span> <span class="letter">b</span>
      <span class="letter">o</span> <span class="letter">u</span>
      <span class="letter">t</span> <span class="letter">&nbsp;</span>
      <span class="letter">t</span> <span class="letter">h</span>
      <span class="letter">i</span> <span class="letter">s</span>
      <span class="letter">&nbsp;</span> <span class="letter">p</span>
      <span class="letter">r</span> <span class="letter">o</span>
      <span class="letter">j</span> <span class="letter">e</span>
      <span class="letter">c</span> <span class="letter">t</span>
    </h1>
    <p class="text">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cupiditate, iste
      aut. Velit sapiente deleniti voluptate repellat error. Suscipit, alias
      error aspernatur obcaecati quas, animi magnam quo nulla voluptates
      expedita pariatur.
    </p>
  </div>
</template>

<script>
import anime from 'animejs';

export default {
  name: 'About',
  mounted() {
    anime
      .timeline({ loop: true })
      .add({
        targets: '.ml12 .letter',
        translateX: [40, 0],
        translateZ: 0,
        opacity: [0, 1],
        easing: 'easeOutExpo',
        duration: 1200,
        delay: function (el, i) {
          return 500 + 30 * i;
        },
      })
      .add({
        targets: '.ml12 .letter',
        translateX: [0, -30],
        opacity: [1, 0],
        easing: 'easeInExpo',
        duration: 1100,
        delay: function (el, i) {
          return 100 + 30 * i;
        },
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.aboutWrapper {
  background: #f6f6f6;
  max-width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  padding: 50px;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  color: #1e3d4a;

  .nav {
    width: 100%;
    position: absolute;
    top: 20px;

    img.logo,
    img.about {
      max-height: 20px;
    }
    img.logo {
      float: left;
      margin-left: 15px;
    }
    img.about {
      float: right;
      margin-right: 15px;
    }
  }

  .ml12 {
    font-weight: 200;
    font-size: 1.8em;
    text-transform: uppercase;
    letter-spacing: 0.5em;

    .letter {
      display: inline-block;
      line-height: 1em;
    }
  }
}
</style>
