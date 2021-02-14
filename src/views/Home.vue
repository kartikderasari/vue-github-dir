<template>
  <div class="home">
    <v-container fluid class="mt-16">
      <v-row justify="center">
        <v-col cols="8">
          <searchUser />
          <resultUser />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import searchUser from "../components/searchUser";
import resultUser from "../components/resultUser";
export default {
  name: "Home",
  components: { searchUser, resultUser },
};
</script>
