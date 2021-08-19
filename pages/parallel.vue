<template>
  <v-app>
    <Header />
    <v-main>
      <v-container fluid>
        <v-layout wrap>
          <v-flex xs12 sm12 md6 lg6 xl6>
            <div id="home" class="discript left-1">
              <div class="data">
                <h1>Welcome</h1>
                <p>My portfolio site</p>
              </div>
            </div>
          </v-flex>
          <v-flex xs12 sm12 md6 lg6 xl6>
            <div class="column right-1">
              <div class="data" />
            </div>
          </v-flex>
        </v-layout>
        <v-layout wrap>
          <v-flex xs12 sm12 md6 lg6 xl6>
            <div id="about" class="discript left-2">
              <div class="data">
                <h1>About</h1>
                <p>自己紹介</p>
                <p>name:ma-haruyoshi</p>
                <p>hobby:一人旅（今は昔）<br>お笑い観賞</p>
                <p>wish:心身の健康</p>
                <p>worry:子育て</p>
              </div>
            </div>
          </v-flex>
          <v-flex xs12 sm12 md6 lg6 xl6>
            <div class="column right-2">
              <div class="data" />
            </div>
          </v-flex>
          <!-- スキルは、リンクみたいに並べて、選択した内容が右に表示されるように。別のが選択されたら表示切替 -->
          <!-- 写真は、リンクみたいに並べて（都市別）、選択した内容が右にスライドで表示されるように。別のが選択されたら表示切替 -->
          <!-- ヘッダーにカテゴリリンク貼る。変な隙間ができるけど・・・ -->
        </v-layout>
        <v-layout wrap>
          <v-flex xs12 sm12 md6 lg6 xl6>
            <div id="skills" class="discript left-3">
              <div class="data">
                <h1>Skills</h1>
                <p>今まで仕事で経験した言語</p>
                <br>
                <a v-scroll-to="'#skilltext'" href="#">
                  <v-btn
                    v-for="(btndata,i) in itemsSkill"
                    :key="i"
                    depressed
                    class="mx-2"
                    color="white"
                    fab
                    large
                    @click="showLang = btndata.lang"
                  >
                    <div v-if="btndata.langicon" !="">
                      <v-icon>
                        <!-- アイコン -->
                        {{ btndata.langicon }}
                      </v-icon>
                    </div>
                    <div v-else>
                      <!-- アイコン無し、略称 -->
                      {{ btndata.shrotlang }}
                    </div>
                  </v-btn>
                </a>
              </div>
            </div>
          </v-flex>
          <v-flex xs12 sm12 md6 lg6 xl6>
            <div id="skilltext" class="discript right-3">
              <div
                v-for="(data,i) in itemsSkill"
                :key="i"
              >
                <div v-if="showLang == data.lang " class="box1">
                  <h2 class="text-left skill">
                    <!-- タイトル -->
                    {{ data.lang }}
                  </h2>
                  <!-- 本文 -->
                  <p class="text-left skill">
                    {{ data.text }}
                  </p>
                </div>
              </div>
            </div>
          </v-flex>
          <v-flex xs12 sm12 md6 lg6 xl6>
            <div id="gallaly" class="discript left-4">
              <div class="data">
                <h1>Photo</h1>
                <p>撮り溜まった写真</p>
              </div>
            </div>
          </v-flex>
          <v-flex xs12 sm12 md6 lg6 xl6>
            <figure class="discript right-4 relative">
              <v-carousel hide-delimiters>
                <v-carousel-item
                  v-for="(item,i) in itemsGrid"
                  :key="i"
                  :src="item.src"
                >
                  <figcaption class="balloon1-top">
                    <p>{{ item.description }}</p>
                  </figcaption>
                </v-carousel-item>>
              </v-carousel>
            </figure>
          </v-flex>
        </v-layout>
      </v-container>
    </v-main>
  </v-app>
</template>
<script>
import Header from '~/components/Header'

import skillData from '~/assets/skillData.json'
import imageGrid from '~/assets/imageGrid.json'

export default {
  data () {
    return {
      // 画像情報設定
      itemsGrid: imageGrid,
      // スキル情報設定
      itemsSkill: skillData,
      Header,
      showLang: null
    }
  },
  methods: {
  }
}
</script>
<style>
body {
  color: #14171a;
  font-size: 10px;
}

.column {
  height: 100vh;
  width: 100%;
  text-align: center;
  display: flex;
  align-items: flex-end;
  justify-content: center;
}
.discript {
  height: 100vh;
  width: 100%;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
}
.data {
  margin-bottom: 10%;
}
h1 {
  font-size: 4.5rem;
}
p {
  font-size: 1.5rem;
}
.skill {
  font-size: 1.2rem;
  overflow-wrap: anywhere;
}
.box1 {
  border: 2px solid #333;
  border-radius: 400px 15px 100px 15px / 15px 200px 15px 185px;
  padding: 4%;
  max-width: 500px;
}
.right-1 {
  background: url("../static/images/prof.png") no-repeat center;
}
.right-2 {
  background: url("../static/images/hiyoko.png") no-repeat center;
}
.right-3 {
  white-space: pre-line;
  word-wrap: break-word;
}
.right-4 {
  white-space: pre-line;
  word-wrap: break-word;
}
.left-1 {
  background-color: #ffb6b9
}
.left-2 {
  background-color: #fae3d9
}
.left-3 {
  background-color: #bbded6
}
.left-4 {
  background-color: #8ac6d1
}
.v-carousel {
  height: 100vh !important;
}
.v-carousel__item {
  height: 100vh !important;
}
.v-main{
  padding: 64px 0px 0px 0px !important;
}
.relative {
  position: relative;
}
.balloon1-top {
  position: absolute;
  display: inline-block;
  margin: 1.5em 0;
  padding: 7px 10px;
  min-width: 100%;
  font-size: 16px;
  background: rgba(0,0,0,.5);
  bottom: 0px;
  left: 0px;
}
.balloon1-top p {
  color: #ffffff;
  text-align: left;
  font-size: 0.9rem;
  margin: 0;
  padding: 0;
}
.span {
  font-size: 2rem;
}
</style>
