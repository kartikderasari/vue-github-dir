<template>
  <v-container fluid class="py-5">
    <v-row
      class="mt-5"
      v-if="organizations == null || organizations.length == 0"
    >
      <v-col>
        <p class="text-center">
          No organizations to show!
        </p>
      </v-col>
    </v-row>

    <v-row
      v-else
      v-for="(org, index) in organizations"
      :key="index"
      align="center"
      justify="center"
    >
      <v-col cols="2" align="center">
        <v-img :src="org.avatar_url" max-width="50px"> </v-img>
      </v-col>
      <v-col cols="10">
        <h3>
          <a :href="'https://github.com/' + org.login" target="_blank">
            {{ org.login }}
          </a>
        </h3>
        <p>{{ org.description }}</p>
      </v-col>
      <v-col>
        <v-divider></v-divider>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Organizations",
  props: ["organizations"],
};
</script>
