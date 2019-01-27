<template>
  <input
    name="search"
    id="search"
    placeholder="e.g. Titan"
    :class="{ dark }"
    :value="value"
    @input="handleChange"
  />
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
      // default: ""
    },
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
input {
  display: flex;
  margin-top: 50px;
  width: 250px;
  color: white;
  text-align: center;
  font-size: 18px;
  font-weight: 300;
  height: 50px;
  border: 0;
  border-bottom: 1px solid #fff;
  background: none;
  transition: box-shadow 0.3s ease-out;
  position: absolute;
  top: calc(50% + 50px);
  transition: top 0.4s ease-out;

  @media (min-width: 768px) {
    top: calc(50% + 80px);
  }

  @media (min-width: 1024px) {
    font-weight: 400;
  }
}

input:focus {
  outline: none;
  box-shadow: 0 10px 15px -12px rgba(255, 255, 255, 0.5);
}

.dark {
  color: #1e3d4a;
  border-bottom: 1px solid #1e3d4a;
}

input:focus {
  box-shadow: 0 10px 15px -12px rgba(#1e3d4a, 0.2);
}

.wrapper.flexStart {
  input {
    top: 5%;
  }
}
</style>
