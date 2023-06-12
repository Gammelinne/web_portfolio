<template>
  <presentation />
  <formation />
  <experience />
  <project />
  <hobbies />
  <contact />
</template>

<script>
import { defineComponent } from 'vue';
import Presentation from '@/components/Presentation.vue';
import Formation from '@/components/Formation.vue';
import Experience from '@/components/Experience.vue';
import Project from '@/components/Project.vue';
import Hobbies from '@/components/Hobbies.vue';
import Contact from '@/components/Contact.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    Presentation,
    Formation,
    Experience,
    Project,
    Hobbies,
    Contact,
  },
});
</script>

<style scoped>
</style>
