<template>
  <v-app 
  class="App"
  :theme="is_light ? 'light' : 'dark'">
    <v-app-bar app 
    :title="$t('App.Title')"
    >
      <v-spacer></v-spacer>
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