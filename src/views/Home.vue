<template>
  <div class="home">
    <v-container fluid class="mt-16">
      <v-row justify="center">
        <v-col cols="12" lg="8" md="10" sm="11">
          <searchUser
            @childtoParentUserData="getUserData"
            @childtoParentRepo="getRepo"
            @childtoParentOrganizations="getOrganizations"
          />

          <resultUser
            v-if="userData != null"
            :userData="userData"
            :repos="repos"
            :organizations="organizations"
          />
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
    },
    getRepo: function(value) {
      this.repos = value;
    },
    getOrganizations: function(value) {
      this.organizations = value;
    },
  },
};
</script>
