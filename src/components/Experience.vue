<template>
  <div id="Experience">
    <v-container>
      <v-card elevation="3">
        <h1 class="text-center my-5">{{ $t('App.Experience.Title') }}</h1>
        <v-timeline v-if="!is_mobile">
          <v-timeline-item v-for="experience in Experiences" :key="experience.id" color="primary" dot-color="primary"
            size="small">
            <div>
              <v-card variant="outlined" elevation="5" class="mx-5">
                <h2 class="my-5 mx-3">{{ experience.title }}</h2>
                <v-img class="mx-5 my-2" :src="experience.logo" :alt="experience.title" max-width="75" max-height="75">
                </v-img>
                <v-card-subtitle>
                  <h4>{{ experience.location }}</h4>
                </v-card-subtitle>
                <v-card-subtitle>
                  <h4>{{ experience.date }}</h4>
                </v-card-subtitle>
                <v-card-text>
                  <p style="text-align: justify" v-for="description in experience.description.split(' -')"
                    :key="description">- {{ description }}</p>
                </v-card-text>
                <v-card-actions>
                  <v-btn v-if="experience.website" text :href="experience.website"
                    target="_blank"><v-icon>mdi-web</v-icon> {{ $t('App.Experience.Website') }}
                  </v-btn>
                </v-card-actions>
              </v-card>
            </div>
          </v-timeline-item>
        </v-timeline>
        <v-timeline v-else align="start" side="end">
          <v-timeline-item v-for="experience in Experiences" :key="experience.id" color="primary" dot-color="primary"
            size="small">
            <div>
              <v-card variant="outlined" class="mx-2">
                <h2 class="my-2 mx-2">{{ experience.title }}</h2>
                <v-img class="mx-5 my-2" :src="experience.logo" :alt="experience.title" max-width="75" max-height="75">
                </v-img>
                <h6 class="mx-5 my-1">{{ experience.location }}</h6>
                <h6 class="mx-5 my-1">{{ experience.date }}</h6>
                <v-card-text>
                  <p style="text-align: justify" v-for="description in experience.description.split(' -')"
                    :key="description">- {{ description }}</p>
                </v-card-text>
                <v-card-actions>
                  <v-btn v-if="experience.website" text :href="experience.website"
                    target="_blank"><v-icon>mdi-web</v-icon> {{ $t('App.Experience.Website') }}
                  </v-btn>
                </v-card-actions>
              </v-card>
            </div>

          </v-timeline-item>
        </v-timeline>
      </v-card>
    </v-container>
  </div>
</template>
  
<script>

export default {
  name: 'ExperienceComponent',
  data: () => ({
    Experiences: [],
    is_mobile: false
  }),
  watch: {
    '$i18n.locale': {
      handler: function () {
        this.updateExperiences();
      },
      deep: true
    },
  },
  created: function () {
    this.updateExperiences();
    this.is_mobile = window.innerWidth < 900;
    //create listener to update is_mobile
    window.addEventListener('resize', () => {
      this.is_mobile = window.innerWidth < 900;
    });
  },
  methods: {
    updateExperiences() {
      this.Experiences = [
        {
          title: this.$t('App.Experience.Eight.Title'),
          location: this.$t('App.Experience.Eight.Location'),
          website: this.$t('App.Experience.Eight.Website'),
          date: this.$t('App.Experience.Eight.Date'),
          description: this.$t('App.Experience.Eight.Description'),
          logo: require('../assets/images/logo/logo-aalborg.png'),
        },
        {
          title: this.$t('App.Experience.Seven.Title'),
          location: this.$t('App.Experience.Seven.Location'),
          website: this.$t('App.Experience.Seven.Website'),
          date: this.$t('App.Experience.Seven.Date'),
          description: this.$t('App.Experience.Seven.Description'),
          logo: require('../assets/images/logo/crococlublogo.png'),
        },
        {
          title: this.$t('App.Experience.One.Title'),
          location: this.$t('App.Experience.One.Location'),
          website: this.$t('App.Experience.One.Website'),
          date: this.$t('App.Experience.One.Date'),
          description: this.$t('App.Experience.One.Description'),
          logo: require('../assets/images/logo/Qwice.jpeg'),
        },
        {
          title: this.$t('App.Experience.Two.Title'),
          location: this.$t('App.Experience.Two.Location'),
          website: this.$t('App.Experience.Two.Website'),
          date: this.$t('App.Experience.Two.Date'),
          description: this.$t('App.Experience.Two.Description'),
          logo: require('../assets/images/logo/Tdclic.jpeg'),
        },
        {
          title: this.$t('App.Experience.Three.Title'),
          location: this.$t('App.Experience.Three.Location'),
          website: this.$t('App.Experience.Three.Website'),
          date: this.$t('App.Experience.Three.Date'),
          description: this.$t('App.Experience.Three.Description'),
          logo: require('../assets/images/logo/pavillon.jpeg'),
        },
        {
          title: this.$t('App.Experience.Four.Title'),
          location: this.$t('App.Experience.Four.Location'),
          website: this.$t('App.Experience.Four.Website'),
          date: this.$t('App.Experience.Four.Date'),
          description: this.$t('App.Experience.Four.Description'),
          logo: require('../assets/images/logo/logo-festyland.png'),
        },
        {
          title: this.$t('App.Experience.Five.Title'),
          location: this.$t('App.Experience.Five.Location'),
          website: this.$t('App.Experience.Five.Website'),
          date: this.$t('App.Experience.Five.Date'),
          description: this.$t('App.Experience.Five.Description'),
          logo: require('../assets/images/logo/mgm.png'),
        },
        {
          title: this.$t('App.Experience.Six.Title'),
          location: this.$t('App.Experience.Six.Location'),
          website: this.$t('App.Experience.Six.Website'),
          date: this.$t('App.Experience.Six.Date'),
          description: this.$t('App.Experience.Six.Description'),
          logo: require('../assets/images/logo/mgm.png'),
        },
      ]
    }
  },
};
</script>
  
<style scoped>
.responsive-card {
  max-width: 100%;
  margin: 0 auto;
}
</style>