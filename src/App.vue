<template>
  <vue2 msg="vue2"/>
  <vue3 msg="vue3"/>
</template>

<script>
import vue2 from '@/components/vue2.vue';
import vue3 from '@/components/vue3.vue';

export default {
  name: 'App',
  components: {
    vue3,
    vue2,
  },
};
</script>


