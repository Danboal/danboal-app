<template>
  <v-app>
    <v-app-bar fixed app class="white--text">
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <AppVarUserAvatar ref="AppVarUserAvatar" />
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
import AppVarUserAvatar from "../components/AppVarUserAvatar.vue";
export default {
  name: "DefaultLayout",
  components: {
    AppVarUserAvatar,
  },
  data() {
    return {
      title:"Danboal",
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