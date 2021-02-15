<template>
  <div class="home">
    <v-container fluid class="mt-16">
      <v-row justify="center">
        <v-col cols="8">
          <!-- :getUserData="childtoParentUserData(value)"
            :getRepo="childtoParentRepo(value)"
            :getOrganizations="childtoParentOrganizations(value)" -->
          <searchUser @childtoParentUserData="getUserData(value)" />
          <resultUser userData="" repos="" organizations="" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import searchUser from "../components/searchUser";
import resultUser from "../components/resultUser";
export default {
  name: "Home",
  data: () => {
    return {
      userData: null,
      repos: null,
      organizations: null,
    };
  },
  components: { searchUser, resultUser },
  methods: {
    getUserData: function(value) {
      this.userData = value;
      console.log("userData");
      console.log(this.userData);
    },
    getRepo: function(value) {
      this.repos = value;
      console.log("repos");
      console.log(this.repos);
    },
    getOrganizations: function(value) {
      this.organizations = value;
      console.log("organizations");
      console.log(this.organizations);
    },
  },
};
</script>
