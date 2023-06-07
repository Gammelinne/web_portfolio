<template>
  <v-app 
  id="App"
  :theme="is_light ? 'light' : 'dark'">
    <v-app-bar app 
    :title="$t('App.Title')"
    >
      <v-spacer></v-spacer>
      <!-- Catégories : Présentation, formation, expereiences, projet, hobbies-->
      <v-btn @click="goTo('#App')">{{ $t('App.Presentation.FirstTitle') }}</v-btn>
      <v-btn @click="goTo('#Formation')">{{ $t('App.Formation.Title') }}</v-btn>
      <v-btn @click="goTo('#Experience')">{{ $t('App.Experience.Title') }}</v-btn>
      <v-btn @click="goTo('#Project')">{{ $t('App.Project.Title') }}</v-btn>
      <v-btn @click="goTo('#Hobbie')">{{ $t('App.Hobbies.Title') }}</v-btn>

      <v-btn
        icon
        @click="is_light = !is_light"
      >
        <v-icon>{{ is_light ? 'mdi-weather-night' : 'mdi-weather-sunny' }}</v-icon>
      </v-btn>
      <v-btn
        icon
        class="mx-5"
        @click="changeLanguage"
      >
        <v-icon>mdi-translate</v-icon> {{ language === 'en' ? 'fr' : 'en' }}
      </v-btn>
    </v-app-bar>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    language: 'en',
    is_light: true,
  }),
  created() {
    //get data from local storage
    this.language = localStorage.getItem('language') || navigator.language.slice(0, 2) || 'en'; 
    this.is_light = localStorage.getItem('is_light') == 'true' ? true : false;
  },
  methods: {
    changeLanguage() {
      this.language = this.language === 'en' ? 'fr' : 'en';
      localStorage.setItem('language', this.language);
      this.$i18n.locale = this.language;
    },
    goTo(route) {
      window.scroll({
        behavior: 'smooth',
        left: 0,
        top: document.querySelector(route).offsetTop
      });
    }
  },
  watch: {
    is_light() {
      localStorage.setItem('is_light', this.is_light);
    }
  }
}
</script>

<style>
</style>