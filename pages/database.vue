<template>
  <div>
    <Menu class="header"/>
    <div class="header2">
      <v-navigation-drawer app v-model="drawer" >
        <div class="search-field">
          <v-container>
              <div class="search-area">
                <v-btn icon class="drawer-icon" @click.stop="drawer = !drawer">
                  <v-icon>mdi-chevron-right</v-icon>
                </v-btn>
                <v-row class="search-title">
                  <p class="field-title">SEARCH</p>
                </v-row>
                <v-row>
                  <v-text-field v-model="keyword" label="keyword" color="blue-grey lighten-1"></v-text-field>
                </v-row>
              </div>
              <v-row class="filter-title">
                <p class="field-title">FILTER</p>
              </v-row>
              <v-row>
                <div class="filters">
                    <div class="sex">
                    <p class="field-words">Sex</p>
                    <div class="filter-category">
                        <v-switch label="man" v-model="showMan" color="blue-grey lighten-1" class="switch"></v-switch>
                        <v-switch label="woman" v-model="showWoman" color="blue-grey lighten-1" class="switch"></v-switch>
                    </div>
                </div>
                <div class="sex">
                  <p class="field-words">Country</p>
                  <div class="filter-category">
                      <v-switch label="US" v-model="showUs" color="blue-grey lighten-1"  class="switch"></v-switch>
                      <v-switch label="UK" v-model="showUk" color="blue-grey lighten-1"  class="switch"></v-switch>
                      <v-switch label="OTHER" v-model="showOther" color="blue-grey lighten-1"  class="switch"></v-switch>
                  </div>
                </div>
              </div>
              </v-row>
          </v-container>
        </div>
      </v-navigation-drawer>
      <v-app-bar color="grey darken-3" dark app clipped-left>
        <v-btn icon  @click.stop="drawer = !drawer">
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
        <v-toolbar-title>
            <img src="../images/logo.png" @click="$router.push('/')" class="logo">
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-menu offset-y>
          <template v-slot:activator="{ on, attrs }">
              <v-app-bar-nav-icon 
              v-bind="attrs"
              v-on="on"
              class="hamb">
              </v-app-bar-nav-icon>
          </template>
          <v-list>
              <v-list-item
              v-for="(item, i) in items"
              :key="i"
              :to="item.link"
              >
                <v-list-item-title
                class="link">
                {{ item.title }}
                </v-list-item-title>
              </v-list-item>
          </v-list>
        </v-menu>
      </v-app-bar>
    </div>
    <div class="data-wrap">
      <v-navigation-drawer app clipped class="drawer">
        <div class="search-field">
          <v-container>
            <div class="search-area">
              <v-row class="search-title">
                <p class="field-title">SEARCH</p>
              </v-row>
              <v-row>
                <v-text-field v-model="keyword" label="keyword" color="blue-grey lighten-1"></v-text-field>
              </v-row>
            </div>
            <v-row class="filter-title">
              <p class="field-title">FILTER</p>
            </v-row>
            <v-row>
              <div class="filters">
                <div class="sex">
                  <p class="field-words">Sex</p>
                  <div class="filter-category">
                    <v-switch label="man" v-model="showMan" color="blue-grey lighten-1" class="switch"></v-switch>
                    <v-switch label="woman" v-model="showWoman" color="blue-grey lighten-1" class="switch"></v-switch>
                  </div>
                </div>
                  <div class="sex">
                  <p class="field-words">Country</p>
                  <div class="filter-category">
                    <v-switch label="US" v-model="showUs" color="blue-grey lighten-1"  class="switch"></v-switch>
                    <v-switch label="UK" v-model="showUk" color="blue-grey lighten-1"  class="switch"></v-switch>
                    <v-switch label="OTHER" v-model="showOther" color="blue-grey lighten-1"  class="switch"></v-switch>
                  </div>
                </div>
              </div>
            </v-row>
          </v-container>
        </div>
      </v-navigation-drawer>
      <div class="data">
        <v-container>
          <v-row class="artist" 
          v-for="artist in filteredList" 
          :key="artist.id"
          justify="center"
          >
            <v-col cols="12" sm="5" md="4" lg="4">
                <div>
                  <iframe :src="artist.spotify"  frameborder="0" allowtransparency="true" allow="encrypted-media" class="artist-spotify"></iframe>
                </div>
            </v-col>
            <v-col cols="12"  sm="5" md="1" lg="1">
                <div class="artist-data">
                  <h1 class="artist-name">{{artist.name}}<span class="record-label">({{artist.label}})</span></h1>
                  <p>Country:{{artist.country}}</p>
                  <p>Sex:{{artist.sex}}</p>
                </div>
              </v-col>
          </v-row>
        </v-container>
      </div>
    </div>
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
      keyword:'',
      showMan: false,
      showWoman: false,
      showUs:false,
      showUk:false,
      showOther:false,
      items:[
        {   
            title:'SONGS',
            link:'/songs' 
        },
        {   
            title:'DATABASE',
            link:'/database' 
        },
        {   
            title:'ABOUT',
            link:'/about' 
        }
      ],
      drawer: false,
    }
  },
  computed:{
    filteredList() {
      let newList = [];
      let newMembers = [];        
      for (let i=0; i<this.$store.state.artistdata.artists.length; i++) {
          let isShow = true;
          if (this.showMan && !this.$store.state.artistdata.artists[i].gender) {
            isShow = false;
          }
          if (this.showWoman && this.$store.state.artistdata.artists[i].gender) {
            isShow = false;
          }
          if (this.showWoman && this.showMan) {
            isShow = true;
          }
          if (this.showUs && !this.$store.state.artistdata.artists[i].us) {
            isShow = false;
          }
          if (this.showUk && !this.$store.state.artistdata.artists[i].uk) {
            isShow = false;
          }
          if (this.showOther && !this.$store.state.artistdata.artists[i].other) {
            isShow = false;
          }
          if (isShow) {
            newList.push(this.$store.state.artistdata.artists[i]);
          }
      }
      for(let i in this.$store.state.artistdata.artists) {
          let artist = this.$store.state.artistdata.artists[i];
          if(artist.name.toLowerCase().includes(this.keyword)) {
            newMembers.push(artist);
          }else if(artist.name.toUpperCase().includes(this.keyword)){
            newMembers.push(artist);
          }
      }
      if(newMembers.length == 0){
        return newList;
      } else if(this.keyword){
        return newMembers;
      } else {
        return newList;
      }              
    }
  }
}
</script>

<style>
.data-wrap{
  display:flex;
  border-right:1px solid #fff ;
}
.search-field{
  padding: 20px;
}
.field-title{
  color:#fff;
  background-color: rgba(255, 255, 255, 0.15);
  border-radius: 2px; 
  padding:5px;
}
.header,.header2{
  margin-bottom:68px;
}
.artist-data{
  margin-left: 20px;
}
.artist-name{
  margin-bottom: 20px;
}
.record-label{
  font-size: 20px;
  color:rgba(255, 255, 255, 0.15);
}
.search-area{
  margin-bottom: 30px;
}
.search-title{
  margin-bottom: -10px;
}
.filter-title{
  margin-bottom: 10px;
}
.field-words{
  margin-bottom: -20px;
}
.filter-category{
  margin: 15px;
}
.switch{
  margin-bottom: -10px;
}
.drawer-icon{
  margin-left:170px;
}
.artist-spotify{
  width:300px;
  height:200px;
}
@media (max-width:960px) {
  .artist-name{
    font-size: 20px;
  }
  .artist-data{
    width:80%;
  }
  .record-label{
    font-size: 12px;
  }
}
@media (max-width: 767px) {
  .artist-spotify{
    width:100%;
    height:200px;
  }
  .artist-name{
    font-size: 18px;
  }
  .artist-data{
    width:100%;
  }
  .record-label{
    font-size: 10px;
  }
  .logo{
    margin-left: -50px;
  }
}
@media (min-width: 1025px) {
  .header2{
    display:none;
  }
}
@media (max-width: 1024px) {
  .header,.drawer{
    display:none;
  }
}
</style>