<template>
  <v-app>
    <v-app-bar :clipped-left="clipped" fixed app color="primary">
      <v-toolbar-title v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main color="primary">
      <v-container color="primary">
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app color="primary">
      <span>Nabils24</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      title: "Suitku Game",
    };
  },
};
</script>\

<style scoped>
</style>
