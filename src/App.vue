<template>
  <v-app dark>

    <NavBar :drawer="drawer"/>

    <v-toolbar app fixed clipped-left class="elevation-3">
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title class="headline text-uppercase mr-5">
          <span>Tournament Eagle</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <AddPlayerDialog />
      </v-toolbar-items>
    </v-toolbar>


    <v-content>
      <v-container fluid>

        <router-view/>

      </v-container>
    </v-content>

  </v-app>
</template>

<script>

import NavBar from "./components/NavBar";
import AddPlayerDialog from "./components/AddPlayerDialog";

export default {
  name: 'App',
  data () {
    return {
      drawer: !null,
    }
  },
  components: {
    NavBar,
    AddPlayerDialog

  },
}
</script>

<style>
</style>