<template>
     <v-navigation-drawer :value="drawer" app clipped>
      
       <template>
  <v-card
    class="mx-auto"
    max-width="400"
    tile
  >
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title to="">Popular Movies</v-list-item-title>
      </v-list-item-content>
    </v-list-item>

    <v-list-item two-line>
      <v-list-item-content>
        <v-list-item-title>Popular TV Shows</v-list-item-title>
      </v-list-item-content>
    </v-list-item>
     <v-list-item two-line>
      <v-list-item-content>
        <v-list-item-title>Trending</v-list-item-title>
      </v-list-item-content>
    </v-list-item>
     <v-list-item two-line>
      <v-list-item-content>
        <v-list-item-title>Coming Soon</v-list-item-title>
      </v-list-item-content>
    </v-list-item>
<v-list-item two-line>
      <v-list-item-content>
        <v-list-item-title>Showing Now</v-list-item-title>
      </v-list-item-content>
    </v-list-item>

    <v-list-item three-line>
      <v-list-item-content>
        <v-list-item-title>Watchlist</v-list-item-title>
        <v-list-item-subtitle>
          Favorites
        </v-list-item-subtitle>
        <v-list-item-subtitle>
          
        </v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
  </v-card>
</template>

        </v-navigation-drawer>
</template>
<script>
import { mapGetters } from 'vuex'
export default {
  name: 'Drawer',
  computed: {
      ...mapGetters({
          drawer: 'getDrawer'
      }),
  },
}
</script>
<style scoped>
.mx-auto{
  margin-top: 60px;
}
</style>