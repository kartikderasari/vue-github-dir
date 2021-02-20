<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12" md="12" sm="12" xs="12">
        <v-card class="my-5 pa-4" elevation="2" outlined shaped align="center">
          <v-card-title>Search GitHub users!</v-card-title>
          <v-card-text>
            <v-text-field
              label="User Name"
              placeholder="Enter GitHub User Name"
              outlined
              clearable
              dense
              v-model="searchQ"
            ></v-text-field>
            <v-btn
              color="primary"
              elevation="2"
              outlined
              v-on:click="searchUser()"
            >
              <v-icon left>
                mdi-magnify
              </v-icon>
              Search
            </v-btn>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row>
      <v-col v-if="loading">
        <v-skeleton-loader
          type="list-item-avatar, divider, list-item-three-line"
          :boilerplate="true"
        ></v-skeleton-loader>
      </v-col>
    </v-row>

    <v-snackbar v-model="snackbar" color="danger" :timeout="3000">
      No user found!
      <template v-slot:action="{ attrs }">
        <v-btn color="teal" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </v-container>
</template>

<script>
export default {
  data: () => {
    return {
      searchQ: "",
      baseURL: "https://api.github.com/users/",
      userData: null,
      repos: null,
      organizations: null,
      loading: false,
      snackbar: false,
    };
  },
  methods: {
    async searchUser() {
      this.userData = null;
      this.loading = true;
      await fetch(this.baseURL + this.searchQ)
        .then((res) => res.json())
        .then((data) => {
          this.userData = data;
          if ("login" in this.userData) {
            this.searchUserRepositories();
            this.searchUserOrganizations();
          } else {
            this.snackbar = true;
            console.log("No user found");
          }
        })
        .catch(() => console.log("Error occurred!"));
      this.loading = false;
      this.$emit("childtoParentUserData", this.userData);
    },
    async searchUserRepositories() {
      await fetch(this.baseURL + this.searchQ + "/repos")
        .then((res) => res.json())
        .then((data) => {
          this.repos = data;
        });
      this.$emit("childtoParentRepo", this.repos);
    },
    async searchUserOrganizations() {
      await fetch(this.baseURL + this.searchQ + "/orgs")
        .then((res) => res.json())
        .then((data) => {
          this.organizations = data;
        });
      this.$emit("childtoParentOrganizations", this.organizations);
    },
  },
};
</script>
