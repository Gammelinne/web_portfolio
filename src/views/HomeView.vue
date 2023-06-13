<template>
  <presentation />
  <formation />
  <experience />
  <project />
  <hobbies />
</template>

<script>
import { defineComponent } from 'vue';
import Presentation from '@/components/Presentation.vue';
import Formation from '@/components/Formation.vue';
import Experience from '@/components/Experience.vue';
import Project from '@/components/Project.vue';
import Hobbies from '@/components/Hobbies.vue';

export default defineComponent({
  name: 'HomeView',
  components: {
    Presentation,
    Formation,
    Experience,
    Project,
    Hobbies,
  },
  mounted() {
    //get if there is a query in the route
    const query = this.$route.query;
    console.log(query);
    window.scroll({
      behavior: 'smooth',
      left: 0,
      top: query.route ? document.querySelector(query.route).offsetTop : 0,
    });
  },
});
</script>

<style scoped>
</style>
