<template>
  <div :class="[{ flexStart: step === 1 }, 'wrapper']">
    <transition name="slide">
      <div class="nav" v-if="step === 1">
        <router-link to="/"
          ><img class="logo" src="../assets/logo_small.png"
        /></router-link>
        <router-link to="/about" @click.native="handleLink();"
          ><img class="about" src="../assets/about.png"
        /></router-link>
      </div>
    </transition>

    <transition name="fade"> <HeroImage v-if="step === 0" /> </transition>

    <Claim v-if="step === 0" />

    <SearchInput
      v-model="searchValue"
      @input="handleInput"
      :dark="step === 1"
    />

    <div class="results" v-if="results && !loading && step === 1">
      <Item
        v-for="item in results"
        :item="item"
        :key="item.data[0].nasa_id"
        @click.native="handleModalOpen(item);"
      />
    </div>

    <div class="loader" v-if="step === 1 && loading">
      <div></div>
      <div></div>
    </div>

    <Modal
      v-if="modalOpen"
      :item="modalItem"
      @closeModal="modalOpen = false;"
    />
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '../components/Claim';
import SearchInput from '../components/SearchInput';
import HeroImage from '../components/HeroImage';
import Item from '../components/Item';
import Modal from '../components/Modal';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'Home',
  components: {
    Claim,
    SearchInput,
    HeroImage,
    Item,
    Modal
  },
  data() {
    return {
      modalOpen: false,
      modalItem: null,
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleLink() {
      this.step = 0;
      this.results = [];
      this.searchValue = '';
    },
    handleModalOpen(item) {
      this.modalOpen = true;
      this.modalItem = item;
    },
    handleInput: debounce(function () {
      this.loading = true;
      axios
        .get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
          this.loading = false;
          this.step = 1;
          console.log('Status: ' + response.status);
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>
.loader {
  display: inline-block;
  position: relative;
  top: 50%;
  width: 64px;
  height: 64px;

  @media (min-width: 768px) {
    width: 90px;
    height: 90px;
  }
}
.loader div {
  position: absolute;
  border: 4px solid #1e3d4a;
  opacity: 1;
  border-radius: 50%;
  animation: loading 1s cubic-bezier(0, 0.2, 0.8, 1) infinite;
}
.loader div:nth-child(2) {
  animation-delay: -0.5s;
}
@keyframes loading {
  0% {
    top: 28px;
    left: 28px;
    width: 0;
    height: 0;
    opacity: 1;
  }
  100% {
    top: -1px;
    left: -1px;
    width: 58px;
    height: 58px;
    opacity: 0;
  }
}

@media (min-width: 768px) {
  @keyframes loading {
    0% {
      top: 40px;
      left: 40px;
      width: 0;
      height: 0;
      opacity: 1;
    }
    100% {
      top: -1px;
      left: -1px;
      width: 81px;
      height: 81px;
      opacity: 0;
    }
  }
}

.wrapper {
  margin: 0;
  width: 100%;
  height: 100vh;
  padding: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: relative;

  &.flexStart {
    justify-content: flex-start;
  }

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

  .results {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
    margin-top: 150px;

    @media (min-width: 768px) {
      grid-template-columns: 1fr 1fr 1fr;
    }
  }
}
</style>
