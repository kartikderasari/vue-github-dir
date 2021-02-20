<template>
  <v-container class="py-5" fluid>
    <v-row class="mt-5" v-if="repos == null">
      <v-col>
        <p class="text-center">
          No repositories to show!
        </p>
      </v-col>
    </v-row>

    <v-row v-else v-for="(repo, index) in repos" :key="index">
      <v-col>
        <h3>
          <a :href="repo.html_url" target="_blank">
            {{ repo.name }}
          </a>
        </h3>
        <p>
          {{ repo.description }}
        </p>

        <p>
          <v-chip
            outlined
            pill
            v-if="repo.language != null"
            small
            :ripple="true"
          >
            {{ repo.language }}
          </v-chip>
          <v-icon small> mdi-star-outline</v-icon> {{ repo.stargazers_count }} |
          <v-icon small>mdi-eye-outline</v-icon>
          {{ repo.watchers_count }} | Last updated on:
          {{ new Date(repo.updated_at).toDateString() }}
        </p>

        <v-divider></v-divider>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Repositories",
  data: () => {
    return {};
  },
  props: ["repos"],
};
</script>
