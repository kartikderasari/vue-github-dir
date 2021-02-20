<template>
  <v-row>
    <v-col cols="12" lg="12" md="12" sm="12">
      <v-card outlined v-if="userData.hasOwnProperty('login')">
        <v-card-text>
          <v-container fluid fill-height>
            <v-row>
              <v-col cols="12" lg="2" md="12" sm="12" align="center">
                <v-avatar size="150">
                  <img :src="userData.avatar_url" />
                </v-avatar>
              </v-col>
              <v-col
                class="text-center text-lg-start text-sm-center"
                align-self="center"
                cols="12"
                lg="10"
                md="12"
                sm="12"
              >
                <h2>{{ userData.name }}</h2>
                <h4>
                  <a
                    class="teal--text text--darken-2 text-decoration-none "
                    :href="userData.html_url"
                    target="_blank"
                  >
                    @{{ userData.login }}</a
                  >
                </h4>
                <p>
                  <a
                    class="teal--text text--darken-2 text-decoration-none "
                    :href="
                      'https://github.com/' + userData.login + '?tab=followers'
                    "
                  >
                    {{ userData.followers }} followers
                  </a>
                  |
                  <a
                    class="teal--text text--darken-2 text-decoration-none "
                    :href="
                      'https://github.com/' + userData.login + '?tab=following'
                    "
                  >
                    {{ userData.following }} following
                  </a>
                </p>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-tabs align-with-title grow>
                  <v-tabs-slider color="primary"></v-tabs-slider>

                  <v-tab href="#repo">
                    Repositories
                  </v-tab>
                  <v-tab href="#orgs">
                    Organizations
                  </v-tab>

                  <v-tab-item id="repo" value="repo">
                    <Repositories :repos="repos" />
                  </v-tab-item>
                  <v-tab-item id="orgs" value="orgs">
                    <Organizations :organizations="organizations" />
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
  props: ["userData", "repos", "organizations"],
};
</script>
