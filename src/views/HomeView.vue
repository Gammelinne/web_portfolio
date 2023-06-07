<template>
  <presentation />
  <formation />
  <experience />
</template>

<script>
import { defineComponent } from 'vue';
import Presentation from '@/components/Presentation.vue';
import Formation from '@/components/Formation.vue';
import Experience from '@/components/Experience.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    Presentation,
    Formation,
    Experience,
  },
});
</script>

<style scoped>
</style>
