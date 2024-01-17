<template>
  <v-card>
    <!-- Create v-table with route values-->
    <v-card-title>
      <h4>{{ $t("App.Routes.Title") }}</h4>
    </v-card-title>
    <v-card-text>
      <v-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-left">{{ $t("App.LahyraRoutes.Table.Method") }}</th>
              <th class="text-left">{{ $t("App.LahyraRoutes.Table.Endpoint") }}</th>
              <th class="text-left">
                {{ $t("App.LahyraRoutes.Table.Description") }}
              </th>
            </tr>
          </thead>
          <tbody v-if="project.title === 'Lahyra'">
            <tr v-for="route in LahyraRoutes" :key="route.id">
              <td>{{ route.method }}</td>
              <td>{{ route.endpoint }}</td>
              <td>{{ route.description }}</td>
            </tr>
          </tbody>
          <tbody v-else-if="project.title === 'WebApp Template'">
            <tr v-for="route in TemplateRoutes" :key="route.id">
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
  name: "RouteComponent",
  props: {
    project: {
      type: Object,
      required: true,
    },
  },
  data: () => ({
    LahyraRoutes: [],
    TemplateRoutes: [],
  }),
  mounted() {
    this.TemplateRoutes = [
      {
        id: 1,
        method: this.$t("App.TemplateRoutes.1.Method"),
        endpoint: this.$t("App.TemplateRoutes.1.Endpoint"),
        description: this.$t("App.TemplateRoutes.1.Description"),
      },
      {
        id: 2,
        method: this.$t("App.TemplateRoutes.2.Method"),
        endpoint: this.$t("App.TemplateRoutes.2.Endpoint"),
        description: this.$t("App.TemplateRoutes.2.Description"),
      },
      {
        id: 3,
        method: this.$t("App.TemplateRoutes.3.Method"),
        endpoint: this.$t("App.TemplateRoutes.3.Endpoint"),
        description: this.$t("App.TemplateRoutes.3.Description"),
      },
      {
        id: 4,
        method: this.$t("App.TemplateRoutes.4.Method"),
        endpoint: this.$t("App.TemplateRoutes.4.Endpoint"),
        description: this.$t("App.TemplateRoutes.4.Description"),
      },
      {
        id: 5,
        method: this.$t("App.TemplateRoutes.5.Method"),
        endpoint: this.$t("App.TemplateRoutes.5.Endpoint"),
        description: this.$t("App.TemplateRoutes.5.Description"),
      },
      {
        id: 6,
        method: this.$t("App.TemplateRoutes.6.Method"),
        endpoint: this.$t("App.TemplateRoutes.6.Endpoint"),
        description: this.$t("App.TemplateRoutes.6.Description"),
      },
      {
        id: 7,
        method: this.$t("App.TemplateRoutes.7.Method"),
        endpoint: this.$t("App.TemplateRoutes.7.Endpoint"),
        description: this.$t("App.TemplateRoutes.7.Description"),
      },
      {
        id: 8,
        method: this.$t("App.TemplateRoutes.8.Method"),
        endpoint: this.$t("App.TemplateRoutes.8.Endpoint"),
        description: this.$t("App.TemplateRoutes.8.Description"),
      },
      {
        id: 9,
        method: this.$t("App.TemplateRoutes.9.Method"),
        endpoint: this.$t("App.TemplateRoutes.9.Endpoint"),
        description: this.$t("App.TemplateRoutes.9.Description"),
      },
      {
        id: 10,
        method: this.$t("App.TemplateRoutes.10.Method"),
        endpoint: this.$t("App.TemplateRoutes.10.Endpoint"),
        description: this.$t("App.TemplateRoutes.10.Description"),
      },
      {
        id: 11,
        method: this.$t("App.TemplateRoutes.11.Method"),
        endpoint: this.$t("App.TemplateRoutes.11.Endpoint"),
        description: this.$t("App.TemplateRoutes.11.Description"),
      },
      {
        id: 12,
        method: this.$t("App.TemplateRoutes.12.Method"),
        endpoint: this.$t("App.TemplateRoutes.12.Endpoint"),
        description: this.$t("App.TemplateRoutes.12.Description"),
      },
      {
        id: 13,
        method: this.$t("App.TemplateRoutes.13.Method"),
        endpoint: this.$t("App.TemplateRoutes.13.Endpoint"),
        description: this.$t("App.TemplateRoutes.13.Description"),
      },
      {
        id: 14,
        method: this.$t("App.TemplateRoutes.14.Method"),
        endpoint: this.$t("App.TemplateRoutes.14.Endpoint"),
        description: this.$t("App.TemplateRoutes.14.Description"),
      },
      {
        id: 15,
        method: this.$t("App.TemplateRoutes.15.Method"),
        endpoint: this.$t("App.TemplateRoutes.15.Endpoint"),
        description: this.$t("App.TemplateRoutes.15.Description"),
      },
      {
        id: 16,
        method: this.$t("App.TemplateRoutes.16.Method"),
        endpoint: this.$t("App.TemplateRoutes.16.Endpoint"),
        description: this.$t("App.TemplateRoutes.16.Description"),
      },
    ];
    this.LahyraRoutes = [
      {
        id: 1,
        method: this.$t("App.LahyraRoutes.1.Method"),
        endpoint: this.$t("App.LahyraRoutes.1.Endpoint"),
        description: this.$t("App.LahyraRoutes.1.Description"),
      },
      {
        id: 2,
        method: this.$t("App.LahyraRoutes.2.Method"),
        endpoint: this.$t("App.LahyraRoutes.2.Endpoint"),
        description: this.$t("App.LahyraRoutes.2.Description"),
      },
      {
        id: 3,
        method: this.$t("App.LahyraRoutes.3.Method"),
        endpoint: this.$t("App.LahyraRoutes.3.Endpoint"),
        description: this.$t("App.LahyraRoutes.3.Description"),
      },
      {
        id: 4,
        method: this.$t("App.LahyraRoutes.4.Method"),
        endpoint: this.$t("App.LahyraRoutes.4.Endpoint"),
        description: this.$t("App.LahyraRoutes.4.Description"),
      },
      {
        id: 5,
        method: this.$t("App.LahyraRoutes.5.Method"),
        endpoint: this.$t("App.LahyraRoutes.5.Endpoint"),
        description: this.$t("App.LahyraRoutes.5.Description"),
      },
      {
        id: 6,
        method: this.$t("App.LahyraRoutes.6.Method"),
        endpoint: this.$t("App.LahyraRoutes.6.Endpoint"),
        description: this.$t("App.LahyraRoutes.6.Description"),
      },
      {
        id: 7,
        method: this.$t("App.LahyraRoutes.7.Method"),
        endpoint: this.$t("App.LahyraRoutes.7.Endpoint"),
        description: this.$t("App.LahyraRoutes.7.Description"),
      },
      {
        id: 8,
        method: this.$t("App.LahyraRoutes.8.Method"),
        endpoint: this.$t("App.LahyraRoutes.8.Endpoint"),
        description: this.$t("App.LahyraRoutes.8.Description"),
      },
      {
        id: 9,
        method: this.$t("App.LahyraRoutes.9.Method"),
        endpoint: this.$t("App.LahyraRoutes.9.Endpoint"),
        description: this.$t("App.LahyraRoutes.9.Description"),
      },
      {
        id: 10,
        method: this.$t("App.LahyraRoutes.10.Method"),
        endpoint: this.$t("App.LahyraRoutes.10.Endpoint"),
        description: this.$t("App.LahyraRoutes.10.Description"),
      },
      {
        id: 11,
        method: this.$t("App.LahyraRoutes.11.Method"),
        endpoint: this.$t("App.LahyraRoutes.11.Endpoint"),
        description: this.$t("App.LahyraRoutes.11.Description"),
      },
      {
        id: 12,
        method: this.$t("App.LahyraRoutes.12.Method"),
        endpoint: this.$t("App.LahyraRoutes.12.Endpoint"),
        description: this.$t("App.LahyraRoutes.12.Description"),
      },
      {
        id: 13,
        method: this.$t("App.LahyraRoutes.13.Method"),
        endpoint: this.$t("App.LahyraRoutes.13.Endpoint"),
        description: this.$t("App.LahyraRoutes.13.Description"),
      },
      {
        id: 14,
        method: this.$t("App.LahyraRoutes.14.Method"),
        endpoint: this.$t("App.LahyraRoutes.14.Endpoint"),
        description: this.$t("App.LahyraRoutes.14.Description"),
      },
      {
        id: 15,
        method: this.$t("App.LahyraRoutes.15.Method"),
        endpoint: this.$t("App.LahyraRoutes.15.Endpoint"),
        description: this.$t("App.LahyraRoutes.15.Description"),
      },
      {
        id: 16,
        method: this.$t("App.LahyraRoutes.16.Method"),
        endpoint: this.$t("App.LahyraRoutes.16.Endpoint"),
        description: this.$t("App.LahyraRoutes.16.Description"),
      },
      {
        id: 17,
        method: this.$t("App.LahyraRoutes.17.Method"),
        endpoint: this.$t("App.LahyraRoutes.17.Endpoint"),
        description: this.$t("App.LahyraRoutes.17.Description"),
      },
      {
        id: 18,
        method: this.$t("App.LahyraRoutes.18.Method"),
        endpoint: this.$t("App.LahyraRoutes.18.Endpoint"),
        description: this.$t("App.LahyraRoutes.18.Description"),
      },
      {
        id: 19,
        method: this.$t("App.LahyraRoutes.19.Method"),
        endpoint: this.$t("App.LahyraRoutes.19.Endpoint"),
        description: this.$t("App.LahyraRoutes.19.Description"),
      },
      {
        id: 20,
        method: this.$t("App.LahyraRoutes.20.Method"),
        endpoint: this.$t("App.LahyraRoutes.20.Endpoint"),
        description: this.$t("App.LahyraRoutes.20.Description"),
      },
      {
        id: 21,
        method: this.$t("App.LahyraRoutes.21.Method"),
        endpoint: this.$t("App.LahyraRoutes.21.Endpoint"),
        description: this.$t("App.LahyraRoutes.21.Description"),
      },
      {
        id: 22,
        method: this.$t("App.LahyraRoutes.22.Method"),
        endpoint: this.$t("App.LahyraRoutes.22.Endpoint"),
        description: this.$t("App.LahyraRoutes.22.Description"),
      },
      {
        id: 23,
        method: this.$t("App.LahyraRoutes.23.Method"),
        endpoint: this.$t("App.LahyraRoutes.23.Endpoint"),
        description: this.$t("App.LahyraRoutes.23.Description"),
      },
      {
        id: 24,
        method: this.$t("App.LahyraRoutes.24.Method"),
        endpoint: this.$t("App.LahyraRoutes.24.Endpoint"),
        description: this.$t("App.LahyraRoutes.24.Description"),
      },
      {
        id: 25,
        method: this.$t("App.LahyraRoutes.25.Method"),
        endpoint: this.$t("App.LahyraRoutes.25.Endpoint"),
        description: this.$t("App.LahyraRoutes.25.Description"),
      },
      {
        id: 26,
        method: this.$t("App.LahyraRoutes.26.Method"),
        endpoint: this.$t("App.LahyraRoutes.26.Endpoint"),
        description: this.$t("App.LahyraRoutes.26.Description"),
      },
      {
        id: 27,
        method: this.$t("App.LahyraRoutes.27.Method"),
        endpoint: this.$t("App.LahyraRoutes.27.Endpoint"),
        description: this.$t("App.LahyraRoutes.27.Description"),
      },
      {
        id: 28,
        method: this.$t("App.LahyraRoutes.28.Method"),
        endpoint: this.$t("App.LahyraRoutes.28.Endpoint"),
        description: this.$t("App.LahyraRoutes.28.Description"),
      },
      {
        id: 29,
        method: this.$t("App.LahyraRoutes.29.Method"),
        endpoint: this.$t("App.LahyraRoutes.29.Endpoint"),
        description: this.$t("App.LahyraRoutes.29.Description"),
      },
      {
        id: 30,
        method: this.$t("App.LahyraRoutes.30.Method"),
        endpoint: this.$t("App.LahyraRoutes.30.Endpoint"),
        description: this.$t("App.LahyraRoutes.30.Description"),
      },
      {
        id: 31,
        method: this.$t("App.LahyraRoutes.31.Method"),
        endpoint: this.$t("App.LahyraRoutes.31.Endpoint"),
        description: this.$t("App.LahyraRoutes.31.Description"),
      },
      {
        id: 32,
        method: this.$t("App.LahyraRoutes.32.Method"),
        endpoint: this.$t("App.LahyraRoutes.32.Endpoint"),
        description: this.$t("App.LahyraRoutes.32.Description"),
      },
      {
        id: 33,
        method: this.$t("App.LahyraRoutes.33.Method"),
        endpoint: this.$t("App.LahyraRoutes.33.Endpoint"),
        description: this.$t("App.LahyraRoutes.33.Description"),
      },
      {
        id: 34,
        method: this.$t("App.LahyraRoutes.34.Method"),
        endpoint: this.$t("App.LahyraRoutes.34.Endpoint"),
        description: this.$t("App.LahyraRoutes.34.Description"),
      },
    ];
  },
};
</script>
