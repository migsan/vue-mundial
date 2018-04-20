<template>
  <v-layout row>
    <v-flex xs12 sm12>
      <v-card color="grey lighten-4" flat>
        <v-card-text>
          <v-subheader>Your Missing</v-subheader>
          <v-container fluid>
            <v-layout row>
              <v-flex xs12>
                <v-text-field
                  name="input-1"
                  label="Label Text"
                  textarea
                  v-model="missing"
                ></v-text-field>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-text>
      </v-card>

      <v-card color="grey lighten-4" flat>
        <v-card-text>
          <v-subheader light>Someone extra</v-subheader>
          <v-container fluid>
            <v-layout row>
              <v-flex xs12>
                <v-text-field
                  name="input-1"
                  label="Label Text"
                  textarea
                  light
                  v-model="have"
                ></v-text-field>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card-text>
      </v-card>

      <v-card flat color="grey lighten-4">
        <v-container fluid>
          <v-layout row>
            <v-flex xs12 text-xs-center>
              <v-btn large @click="compare" color="primary">Compare</v-btn>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card>

      <v-card flat color="grey lighten-4">
        <v-container fluid>
          <v-layout row>
            <v-flex xs12 text-xs-center>
              <span>{{ result }}</span>
            </v-flex>
          </v-layout>
        </v-container>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      have: '',
      missing: '',
      result: []
    }
  },
  methods: {
    compare () {
      console.log('compare stickers!')

      let formattedMissing = this.missing.split(',')
      let formattedHave = this.have.split(',')
      let foundMatches = []

      console.log('formattedMissing: ', formattedMissing)

      for (let i in formattedMissing) {
        if (formattedHave.indexOf(formattedMissing[i]) > -1) {
          foundMatches.push(formattedMissing[i])
        }
      }

      console.log('foundMatches: ', foundMatches)
      this.result = foundMatches;
    }
  }
}
</script>

