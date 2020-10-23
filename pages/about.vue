<template>
<div>
    <Menu class="header"/>
    <v-container>
    <div class="about-wrapper">
        <h1 class="about-title">このサイトについて</h1>
        <p class="about-description">ソウルミュージックの一種であるネオソウルの魅力を広める目的で作成しました。<br>
        このサイトを通じてネオソウルの魅力に触れるきっかけにしていただけたら幸いです。<br>
        使用する全ての音源はSpotifyのリンクになります。
        利用時にSpotifyへログインされていない場合は音源をフルで聴くことはできません。
        </p>
        <h2 class="about-subtitle">SONGS</h2>
        <p class="about-description">私がおすすめするネオソウルナンバーを紹介しています。<br>
        カードをクリックするとそれぞれの雰囲気にぴったりな楽曲を聴くことができます。
        </p>
        <h2 class="about-subtitle">DATABASE</h2>
        <p class="about-description">代表的なネオソウルのアーティストをまとめました。<br>
        表示されるのはアーティストの人気の楽曲トップ10のものとなります。<br>
        ここだけでは紹介しきれていないアーティストもたくさんいるためぜひたくさんのアーティストを探してみてください。
        </p>
    </div>
    </v-container>
</div>
</template>

<script>
export default {

}
</script>

<style>
.header{
    margin-bottom:68px;
}
.about-title{
    margin-bottom: 10px;
}
.about-description{
    line-height: 2;
}
.about-subtitle{
    color:rgb(131, 127, 127);
    border-bottom:1px solid rgb(131, 127, 127);
    margin-bottom: 10px;
    padding-bottom: 10px;
    letter-spacing: 1px;
}

</style>