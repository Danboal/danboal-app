<template>
  <v-app>
    <v-app-bar fixed app class="white--text">
      <v-toolbar-title v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container fluid class="pa-0 ma-0">
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>
<style>
html {
  overflow-y: hidden;
}
</style>
<script>
export default {
  name: "DefaultLayout",
  components: {
  },
  data() {
    return {
      title:"Danboal"
    };
  },
  computed: {
  },
  beforeDestroy() {
  },
  created() {
  },

  mounted() {
  },
  methods: {
  },
};
</script>