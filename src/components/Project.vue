<template>
    <div id="Project">
      <v-container>
        <v-card>
          <h1 class="text-center my-5">{{ $t('App.Project.Title') }}</h1>
          <v-card-text>
            <v-row class="project-row">
              <v-col cols="12" md="6" v-for="(project) in Projects" :key="project.id">
                <v-card class="my-4 project-card">
                  <v-row>
                    <v-col cols="12" md="10">
                      <h4 class="mx-5">{{ project.title }}</h4>
                      <v-card-text>
                        <p>{{ project.location }}</p>
                      </v-card-text>
                      <v-card-text>
                        <p>{{ project.date }}</p>
                      </v-card-text>
                      <v-card-text>
                        <p style="text-align: justify" v-for="description in project.description.split(' -')" :key="description">- {{ description }}</p>
                      </v-card-text>
                    </v-col>
                    <v-col cols="12" md="2">
                      <v-card-title>
                        <h6>{{ project.date }}</h6>
                      </v-card-title>
                    </v-col>
                  </v-row>
                  <v-card-actions>
                    <v-btn
                      text
                      :href="project.website"
                      target="_blank"
                    >
                      <v-icon class="mx-2">mdi-link</v-icon>
                      {{ $t('App.Project.Website') }}
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-col>
            </v-row>
          </v-card-text>
          <h1 class="text-center my-5">{{ $t('App.Project.Github') }}</h1>
          <div class="calendar"></div>
        </v-card>

      </v-container>
    </div>
  </template>
  
  
  
  
  
  
<script>
import GitHubCalendar from 'github-calendar';
import 'github-calendar/dist/github-calendar-responsive.css';

export default {
    name: 'ProjectComponent',
    data() {
        return {
            error: null,
            Projects: [
                {
                    id: 1,
                    title: 'Project 1',
                    location: 'Location 1',
                    date: 'Date 1',
                    description: 'Description 1',
                    website: 'https://www.google.com',
                },
                {
                    id: 2,
                    title: 'Project 2',
                    location: 'Location 2',
                    date: 'Date 2',
                    description: 'Description 2',
                    website: 'https://www.google.com',
                },
                {
                    id: 3,
                    title: 'Project 3',
                    location: 'Location 3',
                    date: 'Date 3',
                    description: 'Description 3',
                    website: 'https://www.google.com',
                },
                {
                    id: 4,
                    title: 'Project 4',
                    location: 'Location 4',
                    date: 'Date 4',
                    description: 'Description 4',
                    website: 'https://www.google.com',
                },
                {
                    id: 5,
                    title: 'Project 5',
                    location: 'Location 5',
                    date: 'Date 5',
                    description: 'Description 5',
                    website: 'https://www.google.com',
                },
                {
                    id: 6,
                    title: 'Project 6',
                    location: 'Location 6',
                    date: 'Date 6',
                    description: 'Description 6',
                    website: 'https://www.google.com',
                },
            ],
        };
    },
    mounted() {
        try {
            GitHubCalendar('.calendar', 'Gammelinne');
        } catch (error) {
            //print toasts of vuetify
            this.error = error;

        }
    },
    methods: {
    },
};
</script>
  
