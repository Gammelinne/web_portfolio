<template>  
  <div id="Presentation">
    <v-container>
      <v-row>
        <v-col cols="12" md="4">
          <v-img class="Avatar mx-auto" src="https://i.ibb.co/4WJD6XR/photo-profile.jpg" width="150" height="150" />
        </v-col>
        <v-col cols="12" md="8">
          <v-card>
            <v-card-text>
              <h2 class="text-center my-3">
                {{ $t('App.Presentation.Title') }}</h2>
              <p>{{ $t('App.Presentation.Description') }} <a href="https://lahyra.com">Lahyra</a></p>
            </v-card-text>
            <v-card-actions>
              <v-btn
                text
                href="https://kylianrenault.lahyra.com/en/assets/Documents/Resume.pdf"
                target="_blank"
                >
              <v-icon>mdi-file-pdf</v-icon>
                {{ $t('App.Presentation.Resume') }}
              </v-btn>
              <v-btn
                text
                href="https://kylianrenault.lahyra.com/en/assets/Documents/Cover%20Letter.pdf"
                target="_blank"
                >
              <v-icon>mdi-file-pdf</v-icon>
                {{ $t('App.Presentation.CoverLetter') }}
              </v-btn>
            </v-card-actions>
            <v-card-actions>
              <v-btn
                text
                href="https://github.com">
              <v-icon>mdi-github</v-icon>
                GitHub
              </v-btn>
              <v-btn
                text
                href="https://www.linkedin.com">
              <v-icon>mdi-linkedin</v-icon>
                LinkedIn
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
      <!--icon scroll down at the bottom center of the page-->
      <v-row justify="center" class="ScrollButton">
        <v-col cols="auto">
         <a
          icon
          @click="scrollTo(this.is_clicked ? '#Presentation' : '#Formation')"
          >
          <v-icon>{{ this.is_clicked ? 'mdi-chevron-double-up' : 'mdi-chevron-double-down' }}</v-icon>
        </a>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'PresentationComponent',
  data: () => ({
    is_clicked: false,
  }),
  watch: {
  },
  methods: {
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
  margin-top: calc(20% - 48px);
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
  position: absolute;
  z-index: 1;
  top: 90vh;
  left: 50%;
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

