<template>
  <v-card class="my-10 pa-4" elevation="2" outlined shaped align="center">
    <v-card-title>Search GitHub users!</v-card-title>
    <v-card-text>
      <v-text-field
        label="User Name"
        placeholder="Enter GitHub User Name"
        outlined
        clearable
        dense
      ></v-text-field>
      <v-btn color="primary" elevation="2" outlined>
        <v-icon left>
          mdi-magnify
        </v-icon>
        Search
      </v-btn>
    </v-card-text>
    <v-card-action> </v-card-action>
  </v-card>
</template>
