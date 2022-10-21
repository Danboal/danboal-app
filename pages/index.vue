<template>
  <v-row>
    <v-col cols="12" xl="4" lg="4" md="3" sm="12" xs="12">
      <v-card
        class="mx-auto"
        max-width="400"
        to="/timeline"
      >
        <v-img
          class="white--text align-end"
          height="200px"
          src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
        >
          <v-card-title>地下闘技場</v-card-title>
        </v-img>
    
        <v-card-subtitle class="pb-0">
          フォローとか関係なし
        </v-card-subtitle>
    
        <v-card-text class="text--primary">
          <div>言いたいことはどんどん言え</div>
        </v-card-text>
    
        <v-card-actions>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage',
  layout: "default",
  middleware: ["auth"],
  data() {
    return {
    }
  },
  mounted(){
    
  }
}
</script>
