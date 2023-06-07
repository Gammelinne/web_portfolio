<template>
  <presentation/>
  <formation/>
</template>

<script>
import { defineComponent } from 'vue';
import Presentation from '@/components/Presentation.vue';
import Formation from '@/components/Formation.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    Presentation,
    Formation,
  },
});
</script>

<style scoped>
</style>
