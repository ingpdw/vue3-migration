<template>
  <div class="container">
    <h1>{{ msg }}</h1>
    <p>{{ count }}</p>
    <p>Math.abs = {{ absCount }}</p>
    <button ref="btnInc" @click="onIncrement">+</button>
    <button ref="btnDec" @click="onDecrement">-</button>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0
    };
  },
  props: {
    msg: String,
  },
  computed: {
    absCount() {
      return Math.abs(this.count);
    },
  },
  methods: {
    onIncrement() {
      this.count += 1;
    },
    onDecrement() {
      this.count -= 1;
    },
  },
  mounted() {
    this.count = 3;
    this.$refs.btnInc.textContent = '+1';
    this.$refs.btnDec.textContent = '-1';
  }
};
</script>

<style scoped>
  .container {
    margin: 10px;
  }
  
  button {
    margin: 3px;
  }
</style>
