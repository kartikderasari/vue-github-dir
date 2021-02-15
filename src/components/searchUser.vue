<template>
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
      <v-btn color="primary" elevation="2" outlined v-on:click="searchUser()">
        <v-icon left>
          mdi-magnify
        </v-icon>
        Search
      </v-btn>
    </v-card-text>
  </v-card>
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
      loadUser: false,
    };
  },
  methods: {
    async searchUser() {
      console.log("Helo");
      this.userData = null;

      await fetch(this.baseURL + this.searchQ)
        .then((res) => res.json())
        .then((data) => {
          this.userData = data;
        });

      this.$emit("childtoParentUserData", this.userData);
      if ("login" in this.userData) {
        this.searchUserRepositories();
        this.searchUserOrganizations();
      } else {
        console.log("No user found");
      }
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
