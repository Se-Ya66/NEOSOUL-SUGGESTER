<template>
    <div>
        <v-content class="index"> 
            <v-container>
                <v-row
                justify="center"
                align="center">
                    <div class="wrap">
                        <transition>
                            <h1 v-if="show">NEO-SOUL<br>SUGGESTER</h1>
                        </transition>
                        <p>propose neo-soul music that suits your mood.</p>
                        <p class="btn" @click="$router.push('songs')">TRY</p>
                    </div>
                </v-row>
            </v-container>
        </v-content>
    </div>
</template>

<script>
export default {
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

.index{
    background: url('../images/people.jpg') center center / cover no-repeat fixed;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background-size: cover;
    text-align: center;
}
.index h1 {
    font-size: 6rem;
    line-height: 1;
    color: #ffffff;
    font-family: 'Bitter', serif;
    margin-bottom: 10px;
}
.wrap{
    position: absolute;
    top: 30%;
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
    transition: 0.3s;
}

.btn:hover {
    text-decoration: none;
    background-color: rgba(255, 255, 255, 0.15);
    color: #ffffff;
    cursor: pointer;
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

/* --------------------------------
* responsive
* -------------------------------- */
@media (max-width: 1024px) {
    .index h1 {
        font-size: 120px;
    }
    .wrap{
        position: absolute;
        top: 40%;
    }
    .btn {
        font-size: 14px;
        width: 140px;
    }
}
@media (max-width: 800px) {
    .index h1 {
        font-size: 90px;
    }
    .wrap{
        position: absolute;
        top: 40%;
    }
    .btn {
        font-size: 14px;
        width: 120px;
    }
}
@media (max-width: 767px) {
    .index h1 {
        font-size: 50px;
    }
    .wrap{
        position: absolute;
        top: 40%;
    }
    .btn {
        font-size: 14px;
        width: 120px;
    }
    
}
</style>
