<template>  
  <div id="Presentation">
    <v-container>
      <v-row>
        <v-col cols="12" md="6">
          <v-img class="Avatar mx-auto" src="https://i.ibb.co/4WJD6XR/photo-profile.jpg" width="150" height="150" />
        </v-col>
        <v-col cols="12" md="6">
          <v-card>
            <v-card-text>
              <h2 class="my-3 text-center">
                {{ $t('App.Presentation.Title') }}</h2>
              <p>{{ $t('App.Presentation.Description') }}</p>
            </v-card-text>
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
         <v-btn
          icon
          href="#Skills"
          >
          <v-icon>mdi-chevron-down</v-icon>
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'PresentationComponent',
  data: () => ({
  }),
  watch: {
  },
  methods: {

  },
};

</script>

<style scoped>
#Presentation {
  margin-top: calc(25% - 48px);
}
.Avatar {
  border-radius: 50%;
}

.ScrollButton {
  position: absolute;
  bottom: 20px;
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

