<template>
  <div id="Formation">
    <v-container>
      <v-card elevation="2">
        <v-card-text>
          <h1 class="my-5 text-center">{{ $t('App.Formation.Title') }}</h1>
          <v-card 
          variant="outlined"
          elevation="4" v-for="formation in formations" :key="formation.id" class="my-5">
            <v-row>
              <v-col cols="12" md="12">
                <h3 class="mx-4 mt-4">{{ formation.title }}</h3>              
                <v-img
                class="mx-4 my-2"
                  :src="formation.logo"
                  :alt="formation.title"
                  max-width="75"
                  max-height="75"
                >
                </v-img>
                <v-card-text>
                  <h5>{{ formation.date }}</h5>
                </v-card-text>
                <v-card-text>
                  <p>{{ formation.location }}</p>
                </v-card-text>
                <v-card-text>
                  <v-chip color="primary" class="mr-1 mt-1" v-for="description in formation.description.split(',')" :key="description">{{ description }}</v-chip>
                </v-card-text>
              </v-col>
            </v-row>
            <v-card-actions>
              <v-btn
              plain
              :href="formation.website"
              target="_blank"
              >
              <v-icon class="mx-2">mdi-link</v-icon>
              {{ $t('App.Formation.Website') }}
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
  name: 'FormationComponent',
  data: () => ({
    formations: [],
  }),
  watch: {
    '$i18n.locale': {
      handler: function(){
        this.updateFormations();
      },
      deep: true
    },
  },
  created: function(){
    this.updateFormations();
  },
  methods: {
    updateFormations(){
      this.formations = [
      {
        id: 1,
        title: this.$t('App.Formation.One.Title'),
        location: this.$t('App.Formation.One.Location'),
        website: this.$t('App.Formation.One.Website'),
        date: this.$t('App.Formation.One.Date'),
        description: this.$t('App.Formation.One.Description'),
        logo: require('../assets/images/logo/logocesi.jpg')
      },
      {
        id: 2,
        title: this.$t('App.Formation.Two.Title'),
        location: this.$t('App.Formation.Two.Location'),
        website: this.$t('App.Formation.Two.Website'),
        date: this.$t('App.Formation.Two.Date'),
        description: this.$t('App.Formation.Two.Description'),
        logo: require('../assets/images/logo/logocesi.jpg')
      },
      {
        id: 3,
        title: this.$t('App.Formation.Three.Title'),
        location: this.$t('App.Formation.Three.Location'),
        website: this.$t('App.Formation.Three.Website'),
        date: this.$t('App.Formation.Three.Date'),
        description: this.$t('App.Formation.Three.Description'),
        logo: require('../assets/images/logo/Normandieuniversite.jpeg')
      },
      {
        id: 4,
        title: this.$t('App.Formation.Four.Title'),
        location: this.$t('App.Formation.Four.Location'),
        website: this.$t('App.Formation.Four.Website'),
        date: this.$t('App.Formation.Four.Date'),
        description: this.$t('App.Formation.Four.Description'),
      },
    ]
    }
  },
};
</script>

<style scoped>
@media screen and (min-width: 600px) {
  #Formation {
    margin-top: 14%;
  }
}
@media screen and (max-width: 600px) {
  #Formation {
    margin-top: 40%;
  }
}
</style>