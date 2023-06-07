<template>
    <div id="Experience">
      <v-container>
        <v-card>
          <v-card-text>
            <h1 class="my-5 text-center">{{ $t('App.Experience.Title') }}</h1>
            <v-card v-for="Experience in Experiences" :key="Experience.id" class="my-4">
              <v-row>
                <v-col cols="12" md="8">
                  <v-card-title>
                    <h4>{{ Experience.title }}</h4>
                  </v-card-title>
                  <v-card-text>
                    <v-chip>{{ Experience.location }}</v-chip>
                  </v-card-text>
                </v-col>
                <v-col cols="12" md="4">
                  <v-card-title>
                    <h6>{{ Experience.date }}</h6>
                  </v-card-title>
                  <v-card-text>
                    <p>{{ Experience.description }}</p>
                  </v-card-text>
                </v-col>
              </v-row>
              <v-card-actions>
                <v-btn
                text
                :href="Experience.website"
                target="_blank"
                >
                <v-icon class="mx-2">mdi-link</v-icon>
                {{ $t('App.Experience.Website') }}
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-card-text>
        </v-card>
      </v-container>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ExperienceComponent',
    data: () => ({
      Experiences: []
    }),
    watch: {
      '$i18n.locale': {
        handler: function(){
          this.updateExperiences();
        },
        deep: true
      }
    },
    created: function(){
      this.updateExperiences();
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
      ]
      }
    },
  };
  </script>
  
  <style scoped>
  @media screen and (min-width: 600px) {
    #Experience {
      margin-top: 30%;
    }
  }
  @media screen and (max-width: 600px) {
    #Experience {
      margin-top: 50%;
    }
  }
  </style>