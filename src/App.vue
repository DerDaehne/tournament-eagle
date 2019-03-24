<template>
  <v-app dark>

    <navbar :drawer="drawer"/>

    <v-toolbar app fixed clipped-left class="elevation-3">
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title class="headline text-uppercase mr-5">
          <span>Tournament Eagle</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-dialog v-model="dialog" width="500" persistent>
          <template v-slot:activator="{ on }">
            <v-btn flat v-on="on">Register</v-btn>
          </template>
          <v-card>
            <v-card-title class="headline dark" primary-title>
              Add Player
            </v-card-title>
            <v-card-text>
              <v-text-field v-model="input.nickname" label="Nickname" class="px-5" required></v-text-field>
              <v-text-field v-model="input.firstname" label="First Name" class="px-5" required></v-text-field>
              <v-text-field v-model="input.lastname" label="Last Name" class="px-5" required></v-text-field>
              <div class="text-xs-center">
                <v-rating v-model="input.skilllevel" medium length=10></v-rating>
              </div>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" flat @click="dialog = !dialog">Close</v-btn>
              <v-btn color="success" flat @click="createUser">Submit</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
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

import navbar from "./components/NavBar";
import axios from "axios";

export default {
  name: 'App',
  data () {
    return {
      drawer: !null,
      dialog: null,
      input: {
        firstname: "",
        lastname: "",
        nickname: "",
        skilllevel: 0
      }
    }
  },
  components: {
    navbar
  },
  methods: {
    createUser() {
      axios({ method: "POST", "url": "http://localhost:8080/players", "data": this.input, "headers": { "content-type": "application/json" } }) 
      this.dialog = false
    }
  }
}
</script>

<style>
</style>