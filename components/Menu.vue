<template>
  <div class="header">
    
    <v-app-bar color="grey darken-3" dark app clipped-left>
      
      <v-toolbar-title><img src="../images/logo.png" @click="$router.push('/')"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn text @click="$router.push('songs')">SONGS</v-btn>
        <v-btn text @click="$router.push('database')">DATABASE</v-btn>
        <v-btn text @click="$router.push('about')">ABOUT</v-btn>
      </v-toolbar-items>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  data(){
    return{
        drawer: false
    }
  }
}
</script>

<style>

.title{
  font-family: 'Noto Serif JP', serif;
}
.drawer-description{
  font-size: 10px;
  line-height: 2;
  margin-top:10px;
}
img{
  cursor: pointer;
}

</style>