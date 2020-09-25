<template>
  <Layout>
    <v-container>
      <v-row justify="space-around">
        <v-col sm="6">
          <v-tabs v-model="tab" grow>
            <v-tab>Item One</v-tab>
            <v-tab>Item Two</v-tab>
            <v-tab>Item Three</v-tab>
          </v-tabs>
          <v-row class="justify-space-around">
            <v-card
              v-for="edge in $page.events.edges"
              :key="edge.node.id"
              width="280"
              class="mt-5"
            >
              <v-img
                class="white--text align-end"
                height="200px"
                :src="`http://localhost:1337${edge.node.thumbnail}`"
              >
                <v-card-title>{{ edge.node.title }}</v-card-title>
              </v-img>

              <v-card-subtitle class="pb-0">
                {{ edge.node.date }}
              </v-card-subtitle>

              <v-card-actions>
                <v-btn color="orange" text>More Info</v-btn>
              </v-card-actions>
            </v-card>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </Layout>
</template>

<page-query>
query {
  events: allEvent {
    edges {
      node {
        id
        title
        description
        price
        date
        duration
        thumbnail
        image
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'E-vents',
  },
  data() {
    return {
      tab: 0,
    }
  },
  watch: {
    tab(val) {
      if (this.tab === 0) {
        this.showAllEvents()
      } else {
        this.showEventsByType()
      }
    },
  },
  methods: {
    showAllEvents() {
      console.log('all')
    },
    showEventsByType() {
      console.log('type')
    },
  },
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
