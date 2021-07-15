<template>
  <v-app>
    <header>
      <v-app-bar
        app
        light
      >
        <v-spacer /> <!-- ボタンを右寄せする -->
        <a v-scroll-to="'#home'" href="#">
          <v-btn text large class="font-weight-regular">
            <v-icon left>
              mdi-home
            </v-icon>
          </v-btn>
        </a>
        <a v-scroll-to="'#about'" href="#">
          <v-btn text large class="font-weight-regular">
            <v-icon left>
              mdi-account
            </v-icon>
          </v-btn>
        </a>
        <a v-scroll-to="'#skills'" href="#">
          <v-btn text large class="font-weight-regular">
            <v-icon left>
              mdi-desktop-classic
            </v-icon>
          </v-btn>
        </a>
        <a v-scroll-to="'#gallaly'" href="#">
          <v-btn text large class="font-weight-regular">
            <v-icon left>
              mdi-camera
            </v-icon>
          </v-btn>
        </a>
      </v-app-bar>
    </header>
    <div class="main" align="center">
      <div id="home" class="black-block">
        <h1>Welcome</h1>
        <p>My portfolio site</p>
      </div>
      <div id="about" class="black-block">
        <h1>About</h1>
        <p>自己紹介</p>
        <client-only>
          <vue-sticker :d="100" class-name="good" />
        </client-only>
        <p>name:ma-haruyoshi</p>
        <p>hobby:お笑い観賞</p>
        <p>wish:心身の健康</p>
      </div>
      <div id="skills" class="black-block">
        <h1>Skills</h1>
        <p>今まで仕事で経験した言語</p>
        <ProgressContent :content="itemsSkill" />
      </div>
      <div id="gallaly" class="black-block">
        <h1>Gallaly</h1>
        <p>一人旅で撮りためた写真<br><br></p>
        <ImageContent :content="itemsGrid" />
      </div>
    </div>
    <v-footer app>
      <div class="flex-grow-1" />
      <div>&copy; {{ new Date().getFullYear() }} H_MATSUDA</div>
    </v-footer>
  </v-app>
</template>
<script>
// 画像一覧表示コンポーネント
import VueSticker from 'vue-sticker'
import ImageContent from '~/components/ImageContent'
import ProgressContent from '~/components/ProgressContent'

import imageGrid from '~/assets/imageGrid.json'
import skillData from '~/assets/skillData.json'

export default {
  components: {
    // コンポーネント定義
    // ImageTopContent,
    ImageContent,
    ProgressContent,
    // Timeline,
    VueSticker
  },
  data () {
    return {
      // 画像情報設定
      itemsGrid: imageGrid,
      // スキル情報設定
      itemsSkill: skillData
    }
  },
  methods: {
  }
}
</script>
<style>
body {
  margin:0px;
}
a {
  text-decoration: none;
}
.color-block {
  background:#afcd68;
  padding:7% 20% 10% 20%;
  color:#fff;
  max-width:800px;
}
.white-block {
  background:#fff;
  padding:7% 20% 10% 20%;
  color:#afcd68;
  max-width:800px;
}
.black-block {
  background:#fff;
  padding:7% 20% 10% 20%;
  color:#707070;
  max-width:800px;
}
h1 {
  text-align:center;
  font-size:60px;
  /*font-family:'wire one', serif;*/
  font-weight:normal;
  max-width:800px;
}
p {
  font-size:20px;
  /*font-family:'Raleway', serif;*/
}
.good__main-image,
.good__backside-image {
  background-color: rgb(250, 248, 248);
  background-size: contain;
  background-image: url("../static/images/prof.png");
}
</style>
