<template>
    <div id="Contact">
        <v-container>
            <v-card elevation="4">
                <h1 class="text-center my-2">{{ $t('App.Contact.Title') }}</h1>
                <v-card-text>
                    <h3 class="my-2">{{ $t('App.Contact.Description') }}</h3>
                </v-card-text>
                <!-- My info -->
                <v-card-text>
                    <v-divider></v-divider>
                    <v-row class="text-center my-3">
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
                            <v-icon>mdi-email</v-icon> kylian.renault@viacesi.fr
                        </v-col>
                        <v-col cols="12" sm="6" md="4">
                            <v-icon>mdi-map-marker</v-icon> Lion-sur-Mer, 14780
                        </v-col>
                        <v-col cols="12" sm="6" md="4">
                            <v-icon>mdi-earth</v-icon> France
                        </v-col>
                        <div class="mx-auto my-3">
                        </div>
                    </v-row>
                    <v-divider></v-divider>
                </v-card-text>
                <!-- Contact form -->
                <v-form @submit.prevent="sendEmail">
                    <v-card-text>
                        <v-text-field class="my-2" v-model="contact.name" :label="$t('App.Contact.Name')"
                            required></v-text-field>
                        <v-text-field class="my-2" v-model="contact.email" :label="$t('App.Contact.Email')" type="email"
                            required :rules="[
                                v => !!v || $t('App.Contact.EmailError'),
                                v => /.+@.+\..+/.test(v) || $t('App.Contact.EmailError')
                            ]"></v-text-field>
                        <v-textarea class="my-2" v-model="contact.message" :label="$t('App.Contact.Message')"
                            required></v-textarea>
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
        Form: []
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
            if (!params.from_name || !params.from_email || !params.message) {
                alert(this.$t('App.Contact.GeneralError'));
                return;
            }
            if (!params.from_email.includes('@') || !params.from_email.includes('.')) {
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
  