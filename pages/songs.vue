<template>
  <div>
    <Menu class="header"/>
    <v-container class="pa-4 text-center">
      <v-row
        class="fill-height"
        align="center"
        justify="center"
      >

        <template v-for="(songlist, i) in songlists">
          <v-col
            cols="12"
            md="4"
            :key="i"
          >
            <v-dialog v-model="songlist.dialog">
              <template v-slot:activator="{ on }">
                <v-card
                v-on="on"
                class="card-btn"
                >
                  <v-img
                    :src='songlist.img'
                    height="225px"
                  >
                    <v-card-title class="title white--text">
                      <v-row
                        class="fill-height flex-column"
                        justify="space-between"
                      >
                        <p class="mt-4 subheading text-left">
                        {{songlist.title}}
                        </p>
                      </v-row>
                    </v-card-title>
                  </v-img>
                </v-card>
              </template>
              <v-card>
                <v-card-title>
                  <span class="headline">{{songlist.title}}</span>
                </v-card-title>
                  <v-container class="pa-4 text-center">
                    <v-row
                    class="fill-height"
                    align="center"
                    justify="center"
                    >
                      <div v-for="(track, i) in songlist.tracks" :key="i">
                      <v-col  cols="12" md="4" >
                        <iframe :src="track" width="300" height="380" frameborder="0" allowtransparency="true" allow="encrypted-media"></iframe>
                      </v-col>
                      </div>
                    </v-row>
                </v-container> 
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn
                    color="blue-grey darken-1"
                    text
                    @click="songlist.dialog = false"
                  >
                    close
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-col>
        </template> 
      
      </v-row>
    </v-container>
  </div>
</template>

<script>
  import Menu from '~/components/Menu.vue'

export default {
  components: {
      Menu,
  },
  data(){
    return{
      songlists:[
        {
          title: 'Dance',
          tracks:[
            "https://open.spotify.com/embed/track/65oeKuWiqXBv6POndjctNL",
            "https://open.spotify.com/embed/track/71XhXay6rKPZCVAaDtFlSR",
            "https://open.spotify.com/embed/track/0jatcRk16ATM6EskYTDH5r",
            "https://open.spotify.com/embed/track/2DOVudVDDa3qibOUcHIafe",
            "https://open.spotify.com/embed/track/5pMZJ7IZEjpuXnTRC5aH57",
            "https://open.spotify.com/embed/track/6DKpDMpKuSHNsisfEVtDMZ"
          ],
          dialog:false,
          img: require('../images/dance.jpg'),
        },
        {
          title: 'Happy',
          tracks:[
            "https://open.spotify.com/embed/track/1lcZPCRAuVXCHSqPsFaWlw",
            "https://open.spotify.com/embed/track/36eTynsQOGbIBwwEGM8j69",
            "https://open.spotify.com/embed/track/5YBepFpRBaXZ4qhSRTZ1cj",
            "https://open.spotify.com/embed/track/2Pw5Y7IXr8yFbNHUF4sTtl",
            "https://open.spotify.com/embed/track/5FNuI8zXGmCsYIGiV5efa4",
            "https://open.spotify.com/embed/track/1JGZ3IqecN7dQwhjSYL06e"
          ],
          dialog:false,
          img: require('../images/happy.jpg'),
        },
        {
          title:"Mellow",
          tracks:[
            "https://open.spotify.com/embed/track/2x28X8t6xaomkkn1ssHJ5E",
            "https://open.spotify.com/embed/track/4eWpJrGhnumxqZHxBgx0B1",
            "https://open.spotify.com/embed/track/0rcuDEcrzF4Zo6ZbUEhaIn",
            "https://open.spotify.com/embed/track/3n79Em8B2VoUGa0nLBPX0D",
            "https://open.spotify.com/embed/track/3Mbcuf19xIPVwec1RFeg44",
            "https://open.spotify.com/embed/track/5IS7qrmK3KCeUJaueAsPdu"
          ],
          dialog:false,
          img: require('../images/mellow.jpg'),
        },
        {
          title:"Drive",
          tracks:[
            "https://open.spotify.com/embed/track/1dt9lIZTptzRIb1GbQXq9p",
            "https://open.spotify.com/embed/track/1wQa9NegotwZHgXqRSuze6",
            "https://open.spotify.com/embed/track/1ON9X3NlL6kWmn3acdLYKM",
            "https://open.spotify.com/embed/track/2fPAn1sRdFyL0CZEmEjRSq",
            "https://open.spotify.com/embed/track/7cZCnBdtChERNYoYxGyLq5",
            "https://open.spotify.com/embed/track/051NZ3rr3HXTULCEySJRX3"
          ],
          dialog:false,
          img: require('../images/drive.jpg'),
        },
        {
          title:"Chill",
          tracks:[
            "https://open.spotify.com/embed/track/6mEIBvPqzDyHt28tPy3jZ0",
            "https://open.spotify.com/embed/track/0y3sgapzF3lTHjN514v2QQ",
            "https://open.spotify.com/embed/track/6qiH0OG98zIT8TXaaQ7L1W",
            "https://open.spotify.com/embed/track/0BIWo58M1rJv9RKmhnNCQT",
            "https://open.spotify.com/embed/track/58dSdjfEYNSxte1aNVxuNf",
            "https://open.spotify.com/embed/track/3vO6tmW02sCdUMtVagBVqG"
          ],
          dialog:false,
          img: require('../images/chill.jpg'),
        },
        {
          title:"Sleep",
          tracks:[
            "https://open.spotify.com/embed/track/1v0PjMzN2vFtK3vTWwASDS",
            "https://open.spotify.com/embed/track/5NisOV1hZza18tlE55DXSr",
            "https://open.spotify.com/embed/track/2fE4MbwX3QGMzNaMjGVhtw",
            "https://open.spotify.com/embed/track/43XbL2ywBerW8or9TSauUS",
            "https://open.spotify.com/embed/track/7zlS5YfwaleDCfWy0RJsL6",
            "https://open.spotify.com/embed/track/6d8BjXoL3dVk4Rsd1rWwCq"
          ],
          dialog:false,
          img: require('../images/sleep.jpg'),
        },
        {
          title:"Ballad",
          tracks:[
            "https://open.spotify.com/embed/track/7hX8jlcBrKk6MMXCxfB6tl",
            "https://open.spotify.com/embed/track/2kR4RhIBa8sE3Xo8HlcAql",
            "https://open.spotify.com/embed/track/6LGwYMXXgURfaequXipzHx",
            "https://open.spotify.com/embed/track/7F2mTYEguu9bzvgwppoJnB",
            "https://open.spotify.com/embed/track/741OE401HO7ZCaPhEqCZ7w",
            "https://open.spotify.com/embed/track/7IsSXaTgBu8ChPx9jLgx28"
          ],
          dialog:false,
          img: require('../images/ballad.jpg'),
        },
        {
          title:"Groovy",
          tracks:[
            "https://open.spotify.com/embed/track/42uCM9saw5B3bCjEFLROlE",
            "https://open.spotify.com/embed/track/74R9xkzhejDki6YOq9QaSn",
            "https://open.spotify.com/embed/track/0OELvYQxTrw8gqY9a2pFaS",
            "https://open.spotify.com/embed/track/2Pvx77sr3wEFnzzwAMPxxG",
            "https://open.spotify.com/embed/track/0mAqtPQ2yZXT9y0WpDov3h",
            "https://open.spotify.com/embed/track/4qIAy5xQbN2N6Xg1O4tslB"
          ],
          dialog:false,
          img: require('../images/groovy.jpg'),
        },
        {
          title:"Reggae",
          tracks:[
            "https://open.spotify.com/embed/track/5sDZFo4TMokdqLoT7mJgOj",
            "https://open.spotify.com/embed/track/6eXNZLPoIikMlKuo1lKBAa",
            "https://open.spotify.com/embed/track/1RRzO2Ny0l17IiHcB6MKKo",
            "https://open.spotify.com/embed/track/7spQoEgL0sf2YVbsgbFaoA",
            "https://open.spotify.com/embed/track/7dgQ4X73bWNVAGFfafhga9",
            "https://open.spotify.com/embed/track/7eDJBFdoSOnXqHUUc5UMaN"
          ],
          dialog:false,
          img: require('../images/reggae.jpg'),
        },
      ]
    }
  }
}
</script>

<style>
.card-btn {
  transition: opacity .4s ease-in-out;
  opacity: 1;
}

.card-btn:hover{
  opacity: 0.7;
  cursor: pointer;
}
.header{
  margin-bottom:80px;
}
</style>