<template>
<div>
    <Menu class="header"/>
    <div class="data-wrap">
    <v-navigation-drawer app clipped>
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
        <ul class="artist" v-for="artist in filteredList" :key="artist.id">
        <v-row>
            <li>
            <div class="artist-list">
            <div class="artist-spotify">
                <iframe :src="artist.spotify" width="300" height="200" frameborder="0" allowtransparency="true" allow="encrypted-media"></iframe>
            </div>
            <div class="artist-data">
                <h1 class="artist-name">{{artist.name}}<span class="record-label">({{artist.label}})</span></h1>
                <p>Country:{{artist.country}}</p>
                <p>Sex:{{artist.sex}}</p>
            </div>
            </div>
            </li>
        </v-row>
        </ul>
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
margin-left:50px ;
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
.header{
margin-bottom:68px;
}

.artist{
list-style: none;
letter-spacing: 1px;
}
.artist-list{
display:flex;
}
.artist-data{
margin-left: 20px;
}
.artist-name{
margin-bottom: 20px;
}
.data{
margin-left:300px;
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

</style>