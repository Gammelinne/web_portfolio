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
            min-height="66"
            @click="goTo(item.route)"
            :prepend-icon="item.icon"
          >
            <v-list-item-title>{{ item.title }}</v-list-item-title>
            <v-divider></v-divider>
        </v-list-item>
        <template v-slot:append>
         <v-footer
            padless
            class="text-center"
          >
           <!--Text to copyright and note the project-->
            <v-col
              cols="12"
            >
              <span>&copy; {{ new Date().getFullYear() }} - {{ $t('App.Title') }}  </span>
            </v-col>

          </v-footer>
        </template>
      </v-navigation-drawer>

    <v-main>
      <router-view/>
    </v-main>

    <v-footer
      padless
      class="text-center"
    >
    <!--github and linkedin btn + copyright at the line-->
      <v-col
        cols="12"
      >
        <v-btn
          class="mx-2"
          href="https://github.com/Gammelinne/"
          target="_blank"
        >
          <v-icon>mdi-github</v-icon>
          GitHub
        </v-btn>
        <v-btn
        class="mx-2"
          href="https://www.linkedin.com/in/kylian-renault/"
          target="_blank"
        >
          <v-icon>mdi-linkedin</v-icon>
          LinkedIn
        </v-btn>
        <span>&copy; {{ new Date().getFullYear() }} - {{ $t('App.Title') }}  </span>
      </v-col>
    </v-footer>
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
    this.updateItems();
  },
  methods: {
    updateItems() {
      this.items = [
        { title: this.$t('App.Presentation.FirstTitle'), icon: 'mdi-home', route: '#App' },
        { title: this.$t('App.Formation.Title'), icon: 'mdi-school', route: '#Formation' },
        { title: this.$t('App.Experience.Title'), icon: 'mdi-briefcase', route: '#Experience' },
        { title: this.$t('App.Project.Title'), icon: 'mdi-rocket', route: '#Project' },
        { title: this.$t('App.Hobbies.Title'), icon: 'mdi-gamepad-variant', route: '#Hobbie' },
        { title: this.$t('App.Contact.Title'), icon: 'mdi-email', route: '#Contact' },
      ]
    },
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
    '$i18n.locale': function() {
        this.updateItems();
      }
  }
}
</script>

<style>
</style>