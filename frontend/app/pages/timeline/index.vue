<template>
  <v-app>
    <custom-header />
    <h1 class="grey--text text--darken-3">TimeLine</h1>
    <v-main>
      <v-form>
        <v-container>
          <v-row>
            <v-col cols="3">
              <v-autocomplete>
              </v-autocomplete> 
            </v-col>
          </v-row>
        </v-container>
      </v-form>

      <v-row justify="center">
        <v-col cols="9">
          <template v-for="point in points">
            <v-row dense>
              <v-col>
                <v-card-title class="pb-0">
                  <v-row>
                    <v-col cols="1" class="text-center">
                      <v-avatar tile color="indigo">
                      </v-avatar>
                    </v-col>
                    <v-col>
                      <span class="subtitle-1">{{ point.sender }}</span>
                    </v-col>
                  </v-row>
                </v-card-title>
              </v-col>
            </v-row>

            <v-row class="mt-n3" dense>
              <v-col offset="1">
                <v-card-text class="pa-0 pl-3">
                  <v-row no-gutters>
                    <v-col cols="9">
                      <v-row dense>
                        <v-col class="pt-0">
                          <span class="text-h6 blue--text text--darken-1"> {{ point.mindtype }}</span>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col class="pt-0">
                          {{ point.comment }}
                        </v-col>
                      </v-row>
                    </v-col>
                    <v-col>
                      <v-row>
                        <v-col class="text-center pb-0">
                          <v-avatar color="indigo" size="64">
                          </v-avatar>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col class="py-0">
                          <v-icon color="grey">
                            mdi-send
                          </v-icon>
                        </v-col>
                      </v-row>
                      <v-row class="mt-n4">
                        <v-col class="text-center pb-0">
                          <div class="text-h6">{{ point.receiver }}</div>
                        </v-col>
                      </v-row>
                    </v-col>
                  </v-row>
                </v-card-text>
              </v-col>
            </v-row>
          </template>
        </v-col>
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import customHeader from '~/components/customHeader.vue'
import axios from 'axios'

export default {
  components: {
    customHeader,
  },
  data: function() {
    return {
      points: [],
    }
  },
  mounted () {
    const response = this.$axios.get('http://localhost:5000/api/v1/points')
      .then(response => (
        this.points = response.data
      ))
    /*
    axios
      .get('/api/v1/points')
      .then(response => (this.points = response.data))
    */
  }
}
</script>