<template>
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
</template>

<script>
import axios from "axios";

export default {
  name: "AddPlayerDialog",
  data () {
    return {
      dialog: null,
      input: {
        firstname: "",
        lastname: "",
        nickname: "",
        skilllevel: 0
      }
    }
  },
  methods: {
    createUser() {
      axios({ method: "POST", "url": "http://localhost:8080/players", "data": this.input, "headers": { "content-type": "application/json" } }) 
      this.input.firstname = ""
      this.input.lastname = "" 
      this.input.nickname = "" 
      this.input.skilllevel = 0
      this.dialog = false
    }
  }

}
</script>
