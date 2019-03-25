<template>
    <v-navigation-drawer v-model="drawer" clipped fixed app>
      <v-list >
        <v-list-tile>
          <v-list-tile-title class="headline pb-1">General</v-list-tile-title>
        </v-list-tile>

        <v-list-tile>
        <v-btn flat block to="#/about">Players</v-btn>
        </v-list-tile>

        <v-list-tile>
        <v-btn flat block to="#/teams">Teams</v-btn>
        </v-list-tile>

        <v-list-tile>
          <v-btn flat block to="#/matches">Matches</v-btn>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
</template>

<script>

export default {
  name: 'NavBar',

  props: {
      drawer: Boolean
  },

  data () {
    return {
      //
    }
  }
}
</script>
