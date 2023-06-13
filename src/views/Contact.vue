<template>
    <div id="Contact">
    <v-container>
    <v-card elevation="4">
      <h1 class="text-center my-2">{{ $t('App.Contact.Title') }}</h1>
        <v-card-text>
            <h3 class=" my-2">{{ $t('App.Contact.Description') }}</h3>
        </v-card-text>
      <v-form @submit.prevent="sendEmail">
        <v-card-text>
            <v-text-field
                class="my-2"
                v-model="contact.name"
                :label="$t('App.Contact.Name')"
                required
            ></v-text-field>
            <v-text-field
              class="my-2"
              v-model="contact.email"
              :label="$t('App.Contact.Email')"
              type="email"
              required
              :rules="[
                  v => !!v || $t('App.Contact.EmailError'),
                  v => /.+@.+\..+/.test(v) || $t('App.Contact.EmailError')
              ]"
              ></v-text-field>
            <v-textarea
                class="my-2"
                v-model="contact.message"
                :label="$t('App.Contact.Message')"
                required
            ></v-textarea>
        </v-card-text>
        <v-card-actions>
            <v-btn type="submit">{{ $t('App.Contact.Submit') }}</v-btn>
        </v-card-actions>
    </v-form>
        </v-card>
    </v-container>
    </div>
  </template>
  
  <script>
import emailjs from '@emailjs/browser'
  
  export default {
    name: 'ContactComponent',
    data: () => ({
      contact: {
        name: null,
        email: null,
        message: null
      },
      Form : []
    }),
    methods: {
      sendEmail() {
        // Configuration d'EmailJS avec votre propre User ID
        emailjs.init('mabGORmh25ApNTL9D');
  
        // Paramètres de l'e-mail à envoyer
        const params = {
          from_name: this.contact.name,
          from_email: this.contact.email,
          message: this.contact.message
        };
  
        // Envoi de l'e-mail via EmailJS
        if(!params.from_name || !params.from_email || !params.message){
          alert(this.$t('App.Contact.GeneralError'));
          return;
        }
        if(!params.from_email.includes('@') || !params.from_email.includes('.')){
          alert(this.$t('App.Contact.EmailError'));
          return;
        }
        emailjs.send('service_5zks746', 'template_zdjau6i', params)
          .then(() => {
            // Réinitialisation du formulaire après l'envoi réussi
            this.contact = {};
            alert(this.$t('App.Contact.Success'));
          })
          .catch((error) => {
            alert(this.$t('App.Contact.CriticError') + ' ' + error);
          });
      },
    },
  };
  </script>
  