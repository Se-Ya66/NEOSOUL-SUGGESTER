<template>
  <div id="index">
    <div id="wrap">
      <div class="content">
        <transition>
            <h1 v-if="show">NEO-SOUL SUGGESTER</h1>
        </transition>
        <p>propose neo-soul music that suits your mood.</p>
        <p class="btn" @click="$router.push('songs')">TRY</p>
      </div>
    </div>
  </div>
</template>

<script>


export default {
  components: {
    
  },
  data(){
    return{
      show: false,
    }
  },
  mounted(){
    this.show = !this.show
  }
}
</script>

<style>
#index {
  margin: 0;
  padding: 0;
  color: #333333;
  font-size: 15px;
  line-height: 2;
}
*, *::before, *::after {
  box-sizing: border-box;
}

p,h1,h2,h3,h4,h5,h6 {
  margin-top: 0;
}

img {
  vertical-align:bottom;
}

#wrap {
  clear: both;
  padding-top: 80px;
  margin-bottom: 178px;
}

.content {
  width: 960px;
  margin: 0 auto;
  text-align: center;
}

#index h1 {
  font-size: 100px;
  line-height: 1;
  color: #ffffff;
  font-family: 'Bitter', serif;
  margin-bottom: 10px;
}

#index .content {
  margin-top: 150px;
}

#index p {
  font-size: 16px;
  color: #ffffff;
}

.btn {
  background-color: transparent;
  color: #ffffff;
  font-size: 20px;
  font-family: 'Bitter', serif;
  text-align: center;
  line-height: 50px;
  margin:50px auto ;
  border-radius: 5px;
  border: 2px solid  #ffffff;
  width: 185px;
  
}

.btn:hover {
  text-decoration: none;
  background-color: rgba(255, 255, 255, 0.15);
  color: #ffffff;
  
  cursor: pointer;
}

#index {
  background-image: url(../images/people.jpg);
  background-repeat: no-repeat;
  background-position: center center;
  background-attachment: fixed;
  background-size: cover;
}
.v-enter-active {
    transition: opacity 3s;
}
.v-enter {
    opacity: 0;
}
.v-enter-to {
    opacity: 1;
}
</style>
