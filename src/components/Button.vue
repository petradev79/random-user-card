<template>
  <button class="btn" @click="btnClick">
    Get random user
  </button>
</template>

<script>
export default {
  props: {
    user: Object
  },
  methods: {
    btnClick() {
      this.$emit('getUser');
    }
  }
};
</script>

<style lang="scss">
.btn {
  cursor: pointer;
  display: inline-block;
  font-family: 'Poppins', sans-serif;
  font-size: 1.5rem;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 0.2rem;
  border: 0;
  border-radius: 0.3rem;
  padding: 1rem 1.5rem;
  transition: transform 0.1s;

  &:focus {
    outline: none;
  }

  &:hover {
    transform: scale(0.98);
  }
}
</style>
