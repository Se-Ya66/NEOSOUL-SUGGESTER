<template>
  <div class="header">
    <v-app-bar color="grey darken-3" dark app clipped-left>
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
      <v-toolbar-items class="nav">
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
        drawer: false,
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
    }
  }
}
</script>

<style>
.link{
    color:#fff;
}
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
.logo{
  margin-left: -30px;
}

/* --------------------------------
* responsive
* -------------------------------- */

@media (min-width:768px) {
    .hamb{
        display: none;
    }
    
}
@media (max-width: 767px) {
    .nav{
      display: none;
    }
    .logo{
      margin-left: -50px;
    }
}

</style>