<template>
  <div id="Project">
    <v-container>
      <v-card elevation="3">
        <h1 class="text-center my-5">{{ $t('App.Project.Github') }}</h1>
        <div class="calendar"></div>
        <h1 class="text-center my-5">{{ $t('App.Project.Title') }}</h1>
        <v-card-text>
          <v-row class="project-row">
            <v-col cols="12" md="12">
              <v-tabs v-model="activeTabIndex" align-tabs="center" color="primary">
                <v-tab v-for="(tab, index) in tabs" :key="index">
                  {{ tab }}
                </v-tab>
              </v-tabs>
            </v-col>
            <v-col cols="12" md="12" v-for="(project) in Projects" :key="project.id">
              <v-card elevation="5" variant="outlined" v-if="activeTabIndex === project.tabIndex">
                <v-card-title>{{ project.title }}</v-card-title>
                <v-card-subtitle class="mx-5">{{ project.date }}</v-card-subtitle>
                <v-card-text>
                  <p>{{ project.location }}</p>
                </v-card-text>
                <v-card-text>
                  <p style="text-align: justify" v-for="description in project.description.split(' -')" :key="description">- {{ description }}</p>
                </v-card-text>
                <v-card-text v-if="project.embed">
                  <embed :src="project.embed" style="width:500px; height: 600px;">
                </v-card-text>
                <v-card-text v-if="project.images">
                  <v-img class="my-2" v-for="image in project.images" :key="image" :src="image" :alt="project.title"></v-img>
                </v-card-text>
                <v-card-actions>
                  <v-btn
                    text
                    :href="project.website"
                    target="_blank"
                  >
                    <v-icon class="mx-2">mdi-github</v-icon>
                    {{ $t('App.Project.Website') }}
                  </v-btn>
                  <v-btn
                    v-if="project.route"
                    @click="dialog = !dialog"
                  >
                    <v-icon class="mx-2">mdi-loupe</v-icon>
                    {{ project.route }}
                  </v-btn>
                </v-card-actions>
                <v-dialog
                  v-if="project.route"
                  v-model="dialog"
                >
                  <route :project="project" />
                </v-dialog>
              </v-card>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import Route from './Route.vue';
import GitHubCalendar from 'github-calendar';
import 'github-calendar/dist/github-calendar-responsive.css';

export default {
  name: 'ProjectComponent',
  components: {
    Route,
  },
  data() {
    return {
      error: null,
      Projects: [],
      dialog: false,
      activeTabIndex: 0,
      tabs: [],
    };
  },
  mounted() {
    try {
      GitHubCalendar('.calendar', 'Gammelinne');
    } catch (error) {
      //print toasts of vuetify
      this.error = error;
    }
    this.updateProjects();
    this.updateTabsTitle();
  },
  watch: {
    '$i18n.locale': {
      handler: function () {
        this.updateProjects();
        this.updateTabsTitle();
      },
      deep: true,
    },
  },
  methods: {
    updateTabsTitle(){
      this.tabs = [
        this.$t('App.Project.One.Title'),
        this.$t('App.Project.Two.Title'),
        this.$t('App.Project.Three.Title'),
        this.$t('App.Project.Four.Title'),
      ]
    },
    updateProjects() {
      this.Projects = [
        {
          id: 1,
          title: this.$t('App.Project.One.Title'),
          date: this.$t('App.Project.One.Date'),
          website: this.$t('App.Project.One.Website'),
          description: this.$t('App.Project.One.Description'),
          route: this.$t('App.Project.One.Route'),
          github: this.$t('App.Project.One.Github'),
          images: [require('../assets/images/Lahyra/lahyrascreen.png')],
          tab: this.$t('App.Project.One.Title'),
          tabIndex: 0,
        },
        {
          id: 2,
          title: this.$t('App.Project.Two.Title'),
          date: this.$t('App.Project.Two.Date'),
          website: this.$t('App.Project.Two.Website'),
          description: this.$t('App.Project.Two.Description'),
          github: this.$t('App.Project.Two.Github'),
          tab: this.$t('App.Project.Two.Title'),
          tabIndex: 1,
        },
        {
          id: 3,
          title: this.$t('App.Project.Three.Title'),
          date: this.$t('App.Project.Three.Date'),
          website: this.$t('App.Project.Three.Website'),
          description: this.$t('App.Project.Three.Description'),
          github: this.$t('App.Project.Three.Github'),
          tab: this.$t('App.Project.Three.Title'),
          tabIndex: 2,
        },
        {
          id: 4,
          title: this.$t('App.Project.Four.Title'),
          date: this.$t('App.Project.Four.Date'),
          website: this.$t('App.Project.Four.Website'),
          description: this.$t('App.Project.Four.Description'),
          github: this.$t('App.Project.Four.Github'),
          tab: this.$t('App.Project.Four.Title'),
          tabIndex: 3,
        },
      ];
    },
  },
};
</script>
