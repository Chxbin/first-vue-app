<template>
  <v-form v-model="valid">
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="name"
            :rules="nameRules"
            :counter="10"
            label="name"
            required
          ></v-text-field>
        </v-col>
        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="Description"
            :rules="nameRules"
            :counter="10"
            label="Description"
            required
          ></v-text-field>
        </v-col>
        dd

        <v-col
          cols="12"
          md="4"
        >
          <v-text-field
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
          ></v-text-field>
        </v-col>
        <div class="text-center">
        <v-btn v-on:click="validate" rounded color="primary" dark>submit</v-btn>
        </div>
      </v-row>
       <v-card max-width="344" class="mx-auto" v-for="(item, index) in todo" v-bind:key="item.id">
          <v-card-title>{{item.name}}</v-card-title>
          <v-card-text>{{item.Description}}</v-card-text>
          <v-card-actions>
          <v-btn v-on:click="Delete(index)" rounded color="primary" dark>Delete</v-btn>
          </v-card-actions>
          </v-card>
          <img src="@/assets/jeu_de_cartes.jpg">

    </v-container>
  </v-form>
</template>

<script>
export default {
  data: () => ({
    valid: false,
    todo: [],
    name: '',
    Description: '',
    nameRules: [
      v => !!v || 'Name is required',
      v => v.length <= 10 || 'Name must be less than 10 characters'
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+/.test(v) || 'E-mail must be valid'
    ]
  }),

  methods: {
    validate: function () {
      this.todo.push({ name: this.name.toString(), Description: this.Description.toString() })
    },

    Delete: function (index) {
      this.todo.splice(index, 1)
    }
  }
}

</script>
