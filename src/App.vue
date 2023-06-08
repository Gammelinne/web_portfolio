<template>
  <v-app 
  id="App"
  :theme="is_light ? 'light' : 'dark'">
    <v-app-bar app 
    >
    <h3 class="mx-5">{{$t('App.Title')}}</h3>
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
        <v-app-bar-nav-icon
          v-if="!is_mobile"
          title="Part"
          :icon="drawer ? 'mdi-close' : 'mdi-menu'"
          @click="drawer = !drawer"
        >
        </v-app-bar-nav-icon>
    </v-app-bar>
    <v-navigation-drawer
        location="right"
        :permanent="!is_mobile"
      >
          <v-list-item
            v-for="item in items"
            :key="item.title"
            link
            @click="goTo(item.route)"
            :prepend-icon="item.icon"
          >
            <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item>
        <template v-slot:append>
         <v-footer
            padless
            class="text-center"
          >
           {{ $t('App.Footer') }}
          </v-footer>
        </template>
      </v-navigation-drawer>

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
    drawer: false,
    is_mobile: true,
    items: [],
  }),
  created() {
    //get data from local storage
    this.language = localStorage.getItem('language') || navigator.language.slice(0, 2) || 'en'; 
    this.is_light = localStorage.getItem('is_light') == 'true' ? true : false;
    this.items = [
      { title: this.$t('App.Presentation.FirstTitle'), icon: 'mdi-home', route: '#App' },
      { title: this.$t('App.Formation.Title'), icon: 'mdi-school', route: '#Formation' },
      { title: this.$t('App.Experience.Title'), icon: 'mdi-briefcase', route: '#Experience' },
      { title: this.$t('App.Project.Title'), icon: 'mdi-rocket', route: '#Project' },
      { title: this.$t('App.Hobbies.Title'), icon: 'mdi-gamepad-variant', route: '#Hobbie' },
      { title: this.$t('App.Contact.Title'), icon: 'mdi-email', route: '#Contact' },
    ]
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
    },
  }
}
</script>

<style>
</style>