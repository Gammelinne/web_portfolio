<template>  
  <div id="Presentation">
    <v-container>
      <v-row>
        <v-col cols="12" md="4">
          <v-img class="Avatar mx-auto" src="../assets/images/Moi.jpeg" width="175" height="175" />
        </v-col>
        <v-col cols="12" md="8">
          <v-card elevation="3">
            <v-card-text>
              <h2 class="text-center my-3">
                {{ $t('App.Presentation.Title') }}</h2>
              <p style="text-align: justify;">{{ $t('App.Presentation.Description') }}<a target="_blank" href="https://lahyra.fr">https://Lahyra.fr</a></p>
            </v-card-text>
            <v-divider></v-divider>
            <v-card-text class="text-center">
              <h3 class="mb-3">{{ $t('App.Contact.Info.Title') }}</h3>
              <v-row>
                <v-col cols="12" sm="6" md="4">
                  <v-icon>mdi-calendar</v-icon> {{ $t('App.Contact.Info.Birthday') }}
                </v-col>
                <v-col cols="12" sm="6" md="4">
                  <v-icon>mdi-account</v-icon> RENAULT Kylian
                </v-col>
                <v-col cols="12" sm="6" md="4">
                  <v-icon>mdi-phone</v-icon> +33 6 67 59 06 50
                </v-col>
                <v-col cols="12" sm="6" md="4">
                  <v-icon>mdi-email</v-icon> <a target="_blank" href="mailto:kylian.renault@viacesi.fr"> kylian.renault@viacesi.fr </a>
                </v-col>
                <v-col cols="12" sm="6" md="4">
                  <v-icon>mdi-map-marker</v-icon> Lion-sur-Mer, 14780
                </v-col>
                <v-col cols="12" sm="6" md="4">
                  <v-icon>mdi-earth</v-icon> France
                </v-col>
              </v-row>
            </v-card-text>
            <v-divider></v-divider>
            <div class="text-center mt-5">
              <!--<v-btn
                class="mx-2 my-1"
                plain
                variant="outlined"
                color="primary"
                href="https://kylianrenault.lahyra.fr/assets/Resume.pdf"
                target="_blank"
                >
              <v-icon>mdi-file-pdf</v-icon>
                {{ $t('App.Presentation.Resume') }}
              </v-btn>
              <v-btn
                class="mx-2 my-1"
                plain
                variant="outlined"
                color="primary"
                href="https://kylianrenault.lahyra.fr/assets/coverletter.pdf"
                target="_blank"
                >
              <v-icon>mdi-file-pdf</v-icon>
                {{ $t('App.Presentation.CoverLetter') }}
              </v-btn>-->
              <v-btn
                class="mx-2 my-1"
                plain
                variant="outlined"
                color="primary"
                href="https://github.com/Gammelinne"
                target="_blank"
                >
              <v-icon>mdi-github</v-icon>
                GitHub
              </v-btn>
              <v-btn
                class="mx-2 my-1"
                plain
                variant="outlined"
                color="primary"
                href="https://www.linkedin.com/in/kylian-renault/"
                target="_blank"
                >
              <v-icon>mdi-linkedin</v-icon>
                LinkedIn
              </v-btn>
            </div>
            <v-card-actions>
             <v-btn
                text
                to="/contact"
                color="primary"
                class="my-5"
              >
              <v-icon class="mx-1">mdi-email</v-icon>
                {{ $t('App.Contact.Title') }}
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
      <!--icon scroll down at the bottom center of the page-->
      <v-container class="ScrollButton">
        <v-row>
          <v-col cols="12" md="12" class="text-center">
            <v-btn icon @click="scrollTo(this.is_clicked ? '#Presentation' : '#Formation')">
              <v-icon>{{ this.is_clicked ? 'mdi-chevron-double-up' : 'mdi-chevron-double-down' }}</v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'PresentationComponent',
  components: {
    
  },
  data: () => ({
    is_clicked: false,
  }),
  created: function(){
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      if (window.scrollY > 700) {
        this.is_clicked = true;
      } else {
        this.is_clicked = false;
      }
    },
    scrollTo(element) {
      if(element == '#Presentation'){
        window.scroll({
          behavior: 'smooth',
          left: 0,
          top: 0,
        });
      } else {
      window.scroll({
        behavior: 'smooth',
        left: 0,
        top: document.querySelector(element).offsetTop,
      });
    }
    this.is_clicked = !this.is_clicked;
    },
  },
};

</script>

<style scoped>
#Presentation {
  margin-top: calc(8% - 48px);
}
.Avatar {
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 0 0 0 5px #fff;
  margin-top: 50%;
}
.v-card-actions {
  justify-content: center;
}
.ScrollButton {
  position: relative;
  z-index: 1;
  margin-top: 8%;
  transform: translateX(-50%);
  cursor: pointer;
  /* animation bouton floating */
  animation: floating 1s ease-in-out infinite;
}

@keyframes floating {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(10px);
  }
  100% {
    transform: translateY(0px);
  }
}
</style>

