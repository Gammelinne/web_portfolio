<template>
<v-card>
    <!-- Create v-table with route values-->
    <v-card-title>
        <h4>{{ $t('App.Routes.Title') }}</h4>
    </v-card-title>
    <v-card-text>
        <v-table>
            <template v-slot:default>
                <thead>
                    <tr>
                        <th class="text-left">{{ $t('App.Routes.Table.Method') }}</th>
                        <th class="text-left">{{ $t('App.Routes.Table.Endpoint') }}</th>
                        <th class="text-left">{{ $t('App.Routes.Table.Description') }}</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="route in Routes" :key="route.id">
                        <td>{{ route.method }}</td>
                        <td>{{ route.endpoint }}</td>
                        <td>{{ route.description }}</td>
                    </tr>
                </tbody>
            </template>
        </v-table>
    </v-card-text>
</v-card>
</template>

<script>
export default {
    name: 'RouteComponent',
    props: {
        project: {
            type: Object,
            required: true,
        },
    },
    data: () => ({
        Routes: [

        ]


    }),
    mounted() {
        this.Routes =  
        [          
            {
                id: 1,
                method: this.$t('App.Routes.1.Method'),
                endpoint: this.$t('App.Routes.1.Endpoint'),
                description: this.$t('App.Routes.1.Description'),
            },
            {
                id: 2,
                method: this.$t('App.Routes.2.Method'),
                endpoint: this.$t('App.Routes.2.Endpoint'),
                description: this.$t('App.Routes.2.Description'),
            },
            {
                id: 3,
                method: this.$t('App.Routes.3.Method'),
                endpoint: this.$t('App.Routes.3.Endpoint'),
                description: this.$t('App.Routes.3.Description'),
            },
            {
                id: 4,
                method: this.$t('App.Routes.4.Method'),
                endpoint: this.$t('App.Routes.4.Endpoint'),
                description: this.$t('App.Routes.4.Description'),
            },
            {
                id: 5,
                method: this.$t('App.Routes.5.Method'),
                endpoint: this.$t('App.Routes.5.Endpoint'),
                description: this.$t('App.Routes.5.Description'),
            },
            {
                id: 6,
                method: this.$t('App.Routes.6.Method'),
                endpoint: this.$t('App.Routes.6.Endpoint'),
                description: this.$t('App.Routes.6.Description'),
            },
            {
                id: 7,
                method: this.$t('App.Routes.7.Method'),
                endpoint: this.$t('App.Routes.7.Endpoint'),
                description: this.$t('App.Routes.7.Description'),
            },
            {
                id: 8,
                method: this.$t('App.Routes.8.Method'),
                endpoint: this.$t('App.Routes.8.Endpoint'),
                description: this.$t('App.Routes.8.Description'),
            },
            {
                id: 9,
                method: this.$t('App.Routes.9.Method'),
                endpoint: this.$t('App.Routes.9.Endpoint'),
                description: this.$t('App.Routes.9.Description'),
            },
            {
                id: 10,
                method: this.$t('App.Routes.10.Method'),
                endpoint: this.$t('App.Routes.10.Endpoint'),
                description: this.$t('App.Routes.10.Description'),
            },
            {
                id: 11,
                method: this.$t('App.Routes.11.Method'),
                endpoint: this.$t('App.Routes.11.Endpoint'),
                description: this.$t('App.Routes.11.Description'),
            },
            {
                id: 12,
                method: this.$t('App.Routes.12.Method'),
                endpoint: this.$t('App.Routes.12.Endpoint'),
                description: this.$t('App.Routes.12.Description'),
            },
            {
                id: 13,
                method: this.$t('App.Routes.13.Method'),
                endpoint: this.$t('App.Routes.13.Endpoint'),
                description: this.$t('App.Routes.13.Description'),
            },
            {
                id: 14,
                method: this.$t('App.Routes.14.Method'),
                endpoint: this.$t('App.Routes.14.Endpoint'),
                description: this.$t('App.Routes.14.Description'),
            },
            {
                id: 15,
                method: this.$t('App.Routes.15.Method'),
                endpoint: this.$t('App.Routes.15.Endpoint'),
                description: this.$t('App.Routes.15.Description'),
            },
            {
                id: 16,
                method: this.$t('App.Routes.16.Method'),
                endpoint: this.$t('App.Routes.16.Endpoint'),
                description: this.$t('App.Routes.16.Description'),
            },
            {
                id: 17,
                method: this.$t('App.Routes.17.Method'),
                endpoint: this.$t('App.Routes.17.Endpoint'),
                description: this.$t('App.Routes.17.Description'),
            },
            {
                id: 18,
                method: this.$t('App.Routes.18.Method'),
                endpoint: this.$t('App.Routes.18.Endpoint'),
                description: this.$t('App.Routes.18.Description'),
            },
            {
                id: 19,
                method: this.$t('App.Routes.19.Method'),
                endpoint: this.$t('App.Routes.19.Endpoint'),
                description: this.$t('App.Routes.19.Description'),
            },
            {
                id: 20,
                method: this.$t('App.Routes.20.Method'),
                endpoint: this.$t('App.Routes.20.Endpoint'),
                description: this.$t('App.Routes.20.Description'),
            },
            {
                id: 21,
                method: this.$t('App.Routes.21.Method'),
                endpoint: this.$t('App.Routes.21.Endpoint'),
                description: this.$t('App.Routes.21.Description'),
            },
            {
                id: 22,
                method: this.$t('App.Routes.22.Method'),
                endpoint: this.$t('App.Routes.22.Endpoint'),
                description: this.$t('App.Routes.22.Description'),
            },
            {
                id: 23,
                method: this.$t('App.Routes.23.Method'),
                endpoint: this.$t('App.Routes.23.Endpoint'),
                description: this.$t('App.Routes.23.Description'),
            },
            {
                id: 24,
                method: this.$t('App.Routes.24.Method'),
                endpoint: this.$t('App.Routes.24.Endpoint'),
                description: this.$t('App.Routes.24.Description'),
            },
            {
                id: 25,
                method: this.$t('App.Routes.25.Method'),
                endpoint: this.$t('App.Routes.25.Endpoint'),
                description: this.$t('App.Routes.25.Description'),
            },
            {
                id: 26,
                method: this.$t('App.Routes.26.Method'),
                endpoint: this.$t('App.Routes.26.Endpoint'),
                description: this.$t('App.Routes.26.Description'),
            },
            {
                id: 27,
                method: this.$t('App.Routes.27.Method'),
                endpoint: this.$t('App.Routes.27.Endpoint'),
                description: this.$t('App.Routes.27.Description'),
            },
            {
                id: 28,
                method: this.$t('App.Routes.28.Method'),
                endpoint: this.$t('App.Routes.28.Endpoint'),
                description: this.$t('App.Routes.28.Description'),
            },
            {
                id: 29,
                method: this.$t('App.Routes.29.Method'),
                endpoint: this.$t('App.Routes.29.Endpoint'),
                description: this.$t('App.Routes.29.Description'),
            },
            {
                id: 30,
                method: this.$t('App.Routes.30.Method'),
                endpoint: this.$t('App.Routes.30.Endpoint'),
                description: this.$t('App.Routes.30.Description'),
            },
            {
                id: 31,
                method: this.$t('App.Routes.31.Method'),
                endpoint: this.$t('App.Routes.31.Endpoint'),
                description: this.$t('App.Routes.31.Description'),
            },
            {
                id: 32,
                method: this.$t('App.Routes.32.Method'),
                endpoint: this.$t('App.Routes.32.Endpoint'),
                description: this.$t('App.Routes.32.Description'),
            },
            {
                id: 33,
                method: this.$t('App.Routes.33.Method'),
                endpoint: this.$t('App.Routes.33.Endpoint'),
                description: this.$t('App.Routes.33.Description'),
            },
            {
                id: 34,
                method: this.$t('App.Routes.34.Method'),
                endpoint: this.$t('App.Routes.34.Endpoint'),
                description: this.$t('App.Routes.34.Description'),
            },
        ]
    },

};
</script>