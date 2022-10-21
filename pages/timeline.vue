<template>
  <v-row>
    <v-col cols="12" xl="12" lg="12" md="12" sm="12" xs="12">
      <v-card
        class="mx-auto"
      >
        <v-list>
          <v-list-item v-for="post in posts">
            <v-list-item-avatar>
              <v-img v-if="post.avatar" :src="post.avatar"></v-img>
            </v-list-item-avatar>
            <v-list-item-title>{{post.name}}<v-list-item-subtitle>{{post.date}}</v-list-item-subtitle></v-list-item-title>
            <div>{{post.text}}</div>
          </v-list-item>
        </v-list>
      </v-card>
      <v-footer
      absolute
      >
        <v-card
          flat
          tile
          width="100%"
          class=""
        >
          <v-card-text class="white--text">
            <v-avatar color="teal" size="48" class="mx-auto">
                <v-img v-if="user.photoURL != null" :src="user.photoURL"></v-img>
                <span v-else class="white--text text-h5">{{user.displayName}}</span>
            </v-avatar>
            <v-btn :disabled="post.text === ''" @click="sendPost">投稿</v-btn>
            <v-textarea v-model="post.text"></v-textarea>
          </v-card-text>
        </v-card>
      </v-footer>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data(){
    return {
      user: this.$store.state.authUser,
      post:{
        uid:"",
        text:"",
        avatar:"",
        name:"",
        date:null,
      },
      posts:[]
    }
  },
  created(){
    this.user = this.$store.state.authUser
  },
  mounted() {
    // RealtimeDatabaseの更新を検知
    this.$fire.database.ref('posts').on('value', (snapshot) => {
      this.posts = snapshot.val();
    })
  },
  methods:{
    sendPost(){
      this.setData()
      this.$fire.database.ref('posts').push(
        this.post
      );
      this.post.text=""
    },
    setData(){
      this.post.uid = this.$store.state.authUser.uid
      this.post.avatar = this.$store.state.authUser.photoURL
      this.post.name = this.$store.state.authUser.displayName
      this.post.date = new Date().toLocaleString('ja-JP', { timeZone: 'Asia/Tokyo' })
    }
  }
}
</script>
