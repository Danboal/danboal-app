<template>
  <v-container>
    <v-card class="mx-auto mt-10" max-width="400" outlined >
      <v-img contain :src="login_view.img"></v-img>
      <v-card-actions class="d-block">
        <v-btn block @click="login" :loading="login_view.loading">LOGIN with Google</v-btn>
      </v-card-actions>
    </v-card>

  </v-container>
</template>

<script>
export default {
  layout: 'empty',
  components: {
  },
  data() {
    return {
      login_view:{
        img:"",
        passwdView:false,
        loading:false,
        err:false
      }
    }
  },
  mounted(){
  },
  methods: {
    async login() {
      const provider = new this.$fireModule.auth.GoogleAuthProvider();
      await this.$fire.auth.signInWithPopup(provider)
        .then((userResult) => {
          console.log(userResult)
          userResult.user.getIdToken(true).then(idToken => {
          })
        })
        .catch((error) => {
          console.error(error)
        });
        
    },
  },
}
</script>