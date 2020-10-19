<template>
  <div class="container">
    <h1>{{ msg }}</h1>
    <p>{{ state.count }}</p>
    <p>Math.abs = {{ state.absCount }}</p>
    <button ref="btnInc" @click="onIncrement">+</button>
    <button ref="btnDec" @click="onDecrement">-</button>
  </div>
</template>

<script>
import { computed, reactive, ref, onMounted } from 'vue';
export default {
  name: 'App',
  props: {
    msg: String,
  },
  setup() {
    const state = reactive({
      count: 0,
      absCount: computed(() => Math.abs(state.count)),
    });
    
    const onIncrement = () => {
      state.count += 1;
    };

    const onDecrement = () => {
      state.count -= 1;
    };

    const btnInc = ref();
    const btnDec = ref();
    onMounted(() => {
      state.count = 3;
      btnInc.value.textContent = '+1';
      btnDec.value.textContent = '-1';
    });

    return {
      state,
      btnInc,
      btnDec,
      onIncrement,
      onDecrement,
    };
  },
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
