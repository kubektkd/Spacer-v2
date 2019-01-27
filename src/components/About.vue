<template>
  <div class="aboutWrapper page">
    <div class="nav">
      <router-link to="/"
        ><img class="logo" src="../assets/logo_small.png" alt="small logo" title="Back to home"
      /></router-link>
      <!-- <router-link to="/about"
        ><img class="about" src="../assets/about.png"
      /></router-link> -->
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
      This is a simple project, which I've done to learn how to build web applications with Vue.js.<br>
    </p>
    <p class="text">
      It uses several basic functionalities of this framework, and it is a modified version of app made in one of video tutorials about Vue.
    </p>
    <!-- <p class="text bottom">
        2019 © AtomicCode.pl - <a href="https://www.atomiccode.pl" target="_blank">profesjonalne strony dla firm</a>
    </p> -->
    <a href="https://www.atomiccode.pl" target="_blank" class="link">
        <div class="box shadow">
            <div class="circle"></div>
            2019 © <span>AtomicCode.pl</span> - professional websites
        </div>
    </a>
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
  width: 100%;
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

  p.text.bottom {
    position: absolute;
    bottom: 20px;
    font-size: 12px;
    
    a {
      text-decoration: none;
      color: #1e3d4a;
      font-style: italic;
      transition: all .5s ease;

      &:hover {
        font-size: 13px;
      }
    }
  }

  a.link {
    text-decoration: none;
    color: #1e3d4a;
    font-size: 11px;
    position: absolute;
    bottom: 20px;

    span {
      font-weight: 600;
    }
  }
  
  .box {
    width: 100%;
    min-width: 250px;
    display: block;
    height: 50px;
    position: relative;
    border-radius: 5px;
    background: linear-gradient(to right, #1e3d4a 0%, #1e3d4a 100%);
    margin-bottom: 40px;
    padding: 18px 15px 5px 45px;
    color: white;
    box-shadow: 1px 2px 1px -1px #777;
    transition: background 200ms ease-in-out;

    &:hover {
      background: linear-gradient(to right, #1e3d4a 35%, #5da4c2 100%);
    }
  }

  .shadow {
    position: relative;

    &:before {
      z-index: -10;
      position: absolute;
      content: "";
      bottom: 20px;
      right: 7px;
      width: 75%;
      top: 0;
      box-shadow: 0 15px 10px #777;
      -webkit-transform: rotate(0deg);
              transform: rotate(0deg);
      transition: all 150ms ease-in-out;

    }
    
    &:hover::before {
      -webkit-transform: rotate(4deg);
              transform: rotate(4deg);
      bottom: 13px;
      z-index: -1;
    }
  }
  
  .circle {
    position: absolute;
    top: 14px;
    left: 15px;
    border-radius: 50%;
    box-shadow: inset 1px 1px 1px 0px rgba(0, 0, 0, 0.5), inset 0 0 0 25px antiquewhite;
    width: 20px;
    height: 20px;
    display: inline-block;
  }
}
</style>
