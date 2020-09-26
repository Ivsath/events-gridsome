<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title>
        <g-link to="/">E-vents</g-link>
      </v-toolbar-title>
      <v-text-field
        placeholder="Search"
        class="ml-8"
        style="max-width: 350px"
        prepend-inner-icon="mdi-magnify"
        outlined
        rounded
        dense
        hide-details
      />
      <v-spacer />
      <v-btn>Create Event</v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-row justify="space-around">
          <v-col sm="6">
            <slot />
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<static-query>
query {
  metadata {
    siteName
    siteDescription
  }
}
</static-query>

<style scoped>
.v-toolbar__title a {
  text-decoration: none;
  color: black;
}
</style>
