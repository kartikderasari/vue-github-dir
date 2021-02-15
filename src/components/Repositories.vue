<template>
  <v-container fluid>
    <p>
      No repositories to show!
    </p>
    <v-row>
      <v-col>
        <h4>
          <a target="_blank">
            repo.name
          </a>
        </h4>
        <p>repo.description</p>

        <small>
          <span>
            repo.language
          </span>
        </small>
        <small> ⭐ repo.stargazers_count </small>
        <small> 👀 repo.watchers_count </small>
        <small>
          Last updated on: new Date(repo.updated_at).toDateString()
        </small>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Repositories",
  data: () => {
    return {
      repo: null,
    };
  },
};
</script>
