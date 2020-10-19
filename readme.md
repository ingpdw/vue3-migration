# vue3-migration

## template

- 여러개의 root Element 선언이 가능

```html
<template>
  <vue2 msg="vue2" />
  <vue3 msg="vue3" />
</template>
```

## setup method

- compositon API의 핵심
- setup method에 data, computed, method, lifecycle hook등을 설정할 수 있음

## data, computed

- setup메소드 내에서 reactive 선언

#### vue2

```javascript
data() {
  return {
    count: 0
  };
},
computed: {
  absCount() {
    return Math.abs(this.count);
  },
},
```

#### vue3

- setup() 내에 정의
- reactive 활용

```javascript
import { computed, reactive } from 'vue';
...
  setup() {
    const state = reactive({
      count: 0,
      absCount: computed(() => Math.abs(state.count)),
    });
...
```

## methods

#### vue2

```javascript
methods: {
  onIncrement() {
    this.count += 1;
  },
  onDecrement() {
    this.count -= 1;
  },
},
```

#### vue3

- setup메소드에 method를 정의

```javascript
const onIncrement = () => {
  state.count += 1;
};

const onDecrement = () => {
  state.count -= 1;
};

setup() {
  return {
    onIncrement,
    onDecrement,
  }
}
```

## lifecycle hook

#### vue2

```javascript
mounted() {
  this.count = 3;
  this.$refs.btnInc.textContent = '+1';
  this.$refs.btnDec.textContent = '-1';
}
```

#### vue3

- lifecycle hook을 setup메소드에 정의

```javascript
setup() {
  const btnInc = ref();
  const btnDec = ref();
  onMounted(() => {
    state.count = 3;
    btnInc.value.textContent = '+1';
    btnDec.value.textContent = '-1';
  });
}
```

## props

#### vue2

```javascript
props: {
  msg: String,
},
methods: {
  onMsg() {
    console.log(this.msg);
  }
}
```

#### vue3

```javascript
props: {
  msg: String,
},
setup(props) {
  return {
    onMsg() {
      console.log(props.msg);
    }
  }
}
```

## emit

#### vue2

```javascript
this.$emit('submit', result);
```

#### vue3

```javascript
setup(props, { emit }) {
  emit('submit', result);
}
```

## sample code

```
yarn
yarn run serve
```
