<template>
    <v-menu
        bottom
        min-width="200px"
        rounded
        offset-y
    >
        <template v-slot:activator="{ on }">
            <v-btn
                icon
                x-large
                v-on="on"
            >
                <v-avatar color="teal" size="48" class="mx-auto">
                    <v-img v-if="user.photoURL" :src="user.photoURL"></v-img>
                    <span v-else-if="!user.photoURL" class="white--text text-h5">{{user.displayName}}</span>
                </v-avatar>
            </v-btn>
        </template>
        <v-card>
            <v-list-item-content class="justify-center">
                <div class="mx-auto text-center">
                    <v-avatar color="teal" size="48" class="mx-auto">
                        <v-img v-if="user.photoURL != null" :src="user.photoURL"></v-img>
                        <span v-else class="white--text text-h5">{{user.displayName}}</span>
                    </v-avatar>
                    <h3>{{ user.displayName }}</h3>
                    <p class="text-caption mt-1"> {{ user.email }}</p>
                    <v-divider class="my-3"></v-divider>
                    <v-btn
                        depressed
                        rounded
                        text
                    >
                        <v-icon>mdi-account-edit</v-icon>
                        プロフィール
                    </v-btn>
                    <v-divider class="my-3"></v-divider>
                    <v-btn
                        depressed
                        rounded
                        text
                        @click="logout"
                    >
                        <v-icon>mdi-logout</v-icon>
                        ログアウト
                    </v-btn>
                </div>
            </v-list-item-content>
        </v-card>
    </v-menu>
</template>

<script>
export default {
  data () {
    return {
      user: this.$store.state.authUser
    }
  },
  beforeDestroy() {
  },
  created(){
    this.user = this.$store.state.authUser
  },
  mounted(){
  },
  methods: {
    async logout(){
        await this.$fire.auth.signOut()
    },

  },
    
}
</script>