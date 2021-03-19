<template>
  <v-app>
    <header>
      <v-app-bar
        app
        light
      >
        <v-spacer /> <!-- ボタンを右寄せする -->
        <a href="#" v-scroll-to="'#home'">
          <v-btn text large class="font-weight-regular">
            <v-icon left>
              mdi-home
            </v-icon>
            Home
          </v-btn>
        </a>
        <a href="#" v-scroll-to="'#about'">
          <v-btn text large class="font-weight-regular">
            <v-icon left>
              mdi-account
            </v-icon>
            About
          </v-btn>
        </a>
        <a href="#" v-scroll-to="'#skills'">
          <v-btn text large class="font-weight-regular">
            <v-icon left>
              mdi-desktop-classic
            </v-icon>
            Skills
          </v-btn>
        </a>
        <a href="#" v-scroll-to="'#gallaly'">
          <v-btn text large class="font-weight-regular">
            <v-icon left>
              mdi-camera
            </v-icon>
            Gallaly
          </v-btn>
        </a>
      </v-app-bar>
    </header>
    <!-- 背景は何かしら動きがほしい -->
    <!-- 背景は固定で、スクロールするとコンテンツが出現するようにしたい -->
    <div class="main" align="center">
      <div class="scallop-up" />
      <div id="home" class="sub color-block">
        <h1>Welcome</h1>
        <p>My portfolio site</p>
      </div>
      <div id="about" class="sub color-block">
        <h1>About</h1>
        <p>自己紹介</p>
        <no-ssr>
          <vue-sticker :d="100" class-name="good" />
        </no-ssr>
        <p>name:ma-haruyoshi</p>
        <p>hobby:一人旅（今は昔）</p>
        <p>wish:心身の健康</p>
      </div>
      <div id="skills" class="sub color-block">
        <h1>Skills</h1>
        <p>今まで仕事で経験した言語</p>
        <ProgressContent />
      </div>
      <div id="gallaly" class="sub color-block">
        <h1>Gallaly</h1>
        <p>一人旅で撮りためた写真</p>
        <ImageContent :content="itemsGrid" />
      </div>
      <div class="scallop-down" />
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

// import imageTop from '~/assets/imageTop.json'
import imageGrid from '~/assets/imageGrid.json'

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
      // TOP画面表示フラグ
      // showTop: true,
      // 一覧画面表示情報
      // itemsCity: [{}],
      // 画像情報設定
      // itemsImage: imageTop,
      // 画像情報設定
      itemsGrid: imageGrid
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
h1 {
  text-align:center;
  font-size:80px;
  font-family:'wire one', serif;
  font-weight:normal;
  max-width:800px;
}
p {
  font-size:20px;
  font-family:'Raleway', serif;
}

/*----------------*/
/*  SCALLOP down  */
/*----------------*/
.scallop-down{
  height:100px;
  max-width:800px;
  background: -webkit-gradient(radial, 50% 0, 10, 50% 0, 40, from(#afcd68), color-stop(0.49, #afcd68), color-stop(0.51, #fff), to(white));
  -webkit-background-size: 49px 100%;
}

/*----------------*/
/*  SCALLOP up    */
/*----------------*/
.scallop-up{
  height:100px;
  max-width:800px;
  background: -webkit-gradient(radial, 50% 100%, 10, 50% 100%, 40, from(#afcd68), color-stop(0.49, #afcd68), color-stop(0.51, #fff), to(white));
  -webkit-background-size: 49px 100%;
}

.good__main-image,
.good__backside-image {
  background-color: rgb(250, 248, 248);
  background-size: contain;
  background-image: url("../static/images/prof.png");
}
</style>
