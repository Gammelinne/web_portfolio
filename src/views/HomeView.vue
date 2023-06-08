<template>
  <presentation />
  <formation />
  <experience />
  <project />
</template>

<script>
import { defineComponent } from 'vue';
import Presentation from '@/components/Presentation.vue';
import Formation from '@/components/Formation.vue';
import Experience from '@/components/Experience.vue';
import Project from '@/components/Project.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    Presentation,
    Formation,
    Experience,
    Project,
  },
});
</script>

<style scoped>
</style>
