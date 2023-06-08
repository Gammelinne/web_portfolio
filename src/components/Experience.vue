<template>
    <div id="Experience">
      <v-container>
        <v-card>
          <h1 class="text-center my-5">{{ $t('App.Experience.Title') }}</h1>          
          <v-timeline
        v-if="!is_mobile"
        >
          <v-timeline-item
            v-for="experience in Experiences"
            :key="experience.id"
            color="primary"
            dot-color="primary"
            size="small"
          >
            <div>
              <v-card variant="outlined" class="mx-5">
                <v-card-title>
                  <h4>{{ experience.title }}</h4>
                </v-card-title>
                <v-card-subtitle>
                  <h4>{{ experience.location }}</h4>
                </v-card-subtitle>
                <v-card-subtitle>
                  <h4>{{ experience.date }}</h4>
                </v-card-subtitle>
                <v-card-text>
                  <p style="text-align: justify" v-for="description in experience.description.split(' -')" :key="description">- {{ description }}</p>
                </v-card-text>
                <v-card-actions>
                  <v-btn
                    v-if="experience.website"
                    text
                    :href="experience.website"
                    target="_blank"
                  ><v-icon>mdi-web</v-icon> {{ $t('App.Experience.Website') }}
                  </v-btn>
                </v-card-actions>
              </v-card>
            </div>
          </v-timeline-item>
        </v-timeline>
        <v-timeline
        v-else
        align="start" side="end"
        >
          <v-timeline-item
            v-for="experience in Experiences"
            :key="experience.id"
            color="primary"
            dot-color="primary"
            size="small"
          >
            <!--hover to see content-->
            <v-tooltip bottom>
              <template v-slot:activator="{ on }">
                <v-btn
                  v-on="on"
                  text
                  size="small"
                > 
                <!--En savoir +-->
                <v-icon>mdi-information</v-icon>
                {{ experience.title }}
                </v-btn>
              </template>
              <span>{{ $t('App.Experience.description') }}</span>
            </v-tooltip>
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
        handler: function(){
          this.updateExperiences();
        },
        deep: true
      },
    },
    created: function(){
      this.updateExperiences();
      this.is_mobile = window.innerWidth < 850;
      //create listener to update is_mobile
      window.addEventListener('resize', () => {
        this.is_mobile = window.innerWidth < 850;
      });
    },
    methods: {
      updateExperiences(){
        this.Experiences = [
        {
          id: 1,
          title: this.$t('App.Experience.One.Title'),
          location: this.$t('App.Experience.One.Location'),
          website: this.$t('App.Experience.One.Website'),
          date: this.$t('App.Experience.One.Date'),
          description: this.$t('App.Experience.One.Description'),
          image: this.$t('App.Experience.One.Image'),
        },
        {
          id: 2,
          title: this.$t('App.Experience.Two.Title'),
          location: this.$t('App.Experience.Two.Location'),
          website: this.$t('App.Experience.Two.Website'),
          date: this.$t('App.Experience.Two.Date'),
          description: this.$t('App.Experience.Two.Description'),
        },
        {
          id: 3,
          title: this.$t('App.Experience.Three.Title'),
          location: this.$t('App.Experience.Three.Location'),
          website: this.$t('App.Experience.Three.Website'),
          date: this.$t('App.Experience.Three.Date'),
          description: this.$t('App.Experience.Three.Description'),
        },
        {
          id: 4,
          title: this.$t('App.Experience.Four.Title'),
          location: this.$t('App.Experience.Four.Location'),
          website: this.$t('App.Experience.Four.Website'),
          date: this.$t('App.Experience.Four.Date'),
          description: this.$t('App.Experience.Four.Description'),
        },
        {
          id: 5,
          title: this.$t('App.Experience.Five.Title'),
          location: this.$t('App.Experience.Five.Location'),
          website: this.$t('App.Experience.Five.Website'),
          date: this.$t('App.Experience.Five.Date'),
          description: this.$t('App.Experience.Five.Description'),
        },
        {
          id: 6,
          title: this.$t('App.Experience.Six.Title'),
          location: this.$t('App.Experience.Six.Location'),
          website: this.$t('App.Experience.Six.Website'),
          date: this.$t('App.Experience.Six.Date'),
          description: this.$t('App.Experience.Six.Description'),
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