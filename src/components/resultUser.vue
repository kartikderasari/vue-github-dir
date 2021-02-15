<template>
  <v-row>
    <v-col>
      <v-card outlined>
        <v-card-text>
          <v-container fluid fill-height>
            <v-row>
              <v-col cols="2">
                <v-avatar color="teal" size="100">
                  <v-icon dark>
                    mdi-account-circle
                  </v-icon>
                </v-avatar>
              </v-col>
              <v-col align-self="center" cols="10">
                <h2>Name</h2>
                <h4>@ahufaohaosdh</h4>
                <p>asdasdasd</p>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-tabs align-with-title grow>
                  <v-tabs-slider color="primary"></v-tabs-slider>

                  <v-tab href="#repo">
                    Repositories
                  </v-tab>
                  <v-tab href="#two">
                    Organizations
                  </v-tab>

                  <v-tab-item id="repo" value="one">
                    <Repositories />
                  </v-tab-item>
                  <v-tab-item id="two" value="two">
                    <Organizations />
                  </v-tab-item>
                </v-tabs>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import Repositories from "../components/Repositories";
import Organizations from "../components/Organizations";
export default {
  components: { Repositories, Organizations },
  data: () => {
    return {
      repo: null,
    };
  },
};
</script>
