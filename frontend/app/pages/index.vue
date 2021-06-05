<template>
  <div id="app">
    <v-app>
      <customHeader />
      <v-main>
        <v-container fluid>
          <router-view />
        </v-container>
      </v-main>
    </v-app>
  </div>
</template>

<script>
import customHeader from '~/components/customHeader.vue'

export default {
  components: {
    customHeader
  },
}
</script>

<style scoped>
p {
  font-size: 2em;
  text-align: center;
}
</style>