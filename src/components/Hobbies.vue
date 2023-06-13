<template>
    <div id="Hobbie">
      <v-container>
        <v-card elevation="3">
          <h1 class="text-center my-5">{{ $t('App.Hobbies.Title') }}</h1>
          <v-card-text>
            <v-row>
              <v-col cols="12" md="6" v-for="hobbie in Hobbies" :key="hobbie.id">
                <v-card variant="outlined" elevation="5">
                  <h1 class="mx-5 my-5 text-center">{{ hobbie.title }}</h1>     
                  <v-card-text>
                    <p style="text-align: justify">{{ hobbie.description }}</p>
                  </v-card-text>
                  <div v-if="hobbie.video">
                    <vue3-wave-audio-player :src="hobbie.video" />
                  </div>
                  <div v-if="hobbie.images">
                    <v-row>
                      <v-col cols="12" md="6" v-for="image in hobbie.images" :key="image">
                        <v-img max-height="150" class="my-4 mx-4" :src="image" :alt="hobbie.title"></v-img>
                      </v-col>
                    </v-row>
                  </div>    
                </v-card>
              </v-col>
            </v-row>
          </v-card-text>
          <div class="text-center">
          <v-btn
            text
            to="/contact"
            color="primary"
            class="my-5"
          >
          <v-icon>mdi-email</v-icon>
            {{ $t('App.Contact.Title') }}
          </v-btn>
        </div>
        </v-card>
      </v-container>
    </div>
  </template>
  
  <script>
  import Vue3WaveAudioPlayer from 'vue3-wave-audio-player'
  export default {
    name: 'HobbiesComponent',
    components: {
        Vue3WaveAudioPlayer
    },
    data() {
      return {
        Hobbies: []
      };
    },
    watch : {
      '$i18n.locale': function() {
        this.updateHobbies();
      }
    },
    methods: {
      updateHobbies(){
        this.Hobbies = [
          {
            id: 1,
            title: this.$t('App.Hobbies.One.Title'),
            images: [require('../assets/images/hobbies/ConcertAvril2023.png'), require('../assets/images/hobbies/ConcertAvril20232.jpg')],
            video: require('../assets/videos/No-surprise-final.wav'),
            description: this.$t('App.Hobbies.One.Description'),
          },
          {
            id: 2,
            title: this.$t('App.Hobbies.Two.Title'),
            images: [require('../assets/images/hobbies/judo.jpg'), require('../assets/images/hobbies/logojudo.jpg')],
            description: this.$t('App.Hobbies.Two.Description'),
          }
        ]
      }
    },
    mounted() {
      this.updateHobbies();
    }
  }
  </script>
  