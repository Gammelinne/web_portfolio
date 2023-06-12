<template>  
  <div id="Presentation">
    <v-container>
      <v-row>
        <v-col cols="12" md="4">
          <v-img class="Avatar mx-auto" src="../assets/images/photo_profile.jpeg" width="150" height="150" />
        </v-col>
        <v-col cols="12" md="8">
          <v-card elevation="3">
            <v-card-text>
              <h2 class="text-center my-3">
                {{ $t('App.Presentation.Title') }}</h2>
              <p style="text-align: justify;">{{ $t('App.Presentation.Description') }} <a target="_blank" href="https://lahyra.com">Lahyra</a></p>
            </v-card-text>
            <v-card-actions>
              <v-btn
                plain
                variant="outlined"
                color="primary"
                href="https://kylianrenault.lahyra.com/en/assets/Documents/Resume.pdf"
                target="_blank"
                >
              <v-icon>mdi-file-pdf</v-icon>
                {{ $t('App.Presentation.Resume') }}
              </v-btn>
              <v-btn
                plain
                variant="outlined"
                color="primary"
                href="https://kylianrenault.lahyra.com/en/assets/Documents/Cover%20Letter.pdf"
                target="_blank"
                >
              <v-icon>mdi-file-pdf</v-icon>
                {{ $t('App.Presentation.CoverLetter') }}
              </v-btn>
            </v-card-actions>
            <v-card-actions>
              <v-btn
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
                plain
                variant="outlined"
                color="primary"
                href="https://www.linkedin.com/in/kylian-renault/"
                target="_blank"
                >
              <v-icon>mdi-linkedin</v-icon>
                LinkedIn
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
      if (window.scrollY > 350) {
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
  margin-top: calc(15% - 48px);
}
.Avatar {
  border-radius: 50%;
  border: 2px solid #fff;
  box-shadow: 0 0 0 5px #fff;
  margin-top: 15%;
}
.v-card-actions {
  justify-content: center;
}
.ScrollButton {
  position: relative;
  z-index: 1;
  margin-top: 20%;
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

