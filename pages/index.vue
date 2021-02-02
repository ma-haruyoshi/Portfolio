<template>
  <v-container class="white">
    <v-row no-gutters justify="center">
      <!-- TOP画面 -->
      <v-col v-for="imgs in itemsImage" :key="imgs.city">
        <div v-if="showTop">
          <v-hover v-slot:default="{ hover }">
            <v-card
              class="mx-auto"
              color="white"
              @click="showGridArea(imgs.city)"
            >
              <v-img
                :aspect-ratio="9/16"
                :src="imgs.src"
              >
                <v-expand-transition>
                  <div
                    v-if="hover"
                    class="d-flex transition-fast-in-fast-out black darken-2 v-card--reveal display-3 white--text"
                  >
                    {{ imgs.city }}
                  </div>
                </v-expand-transition>
              </v-img>
            </v-card>
          </v-hover>
        </div>
      </v-col>
      <transition-group name="fade" tag="div">
        <v-col v-for="imgs in itemsImage" :key="imgs.city">
          <div v-if="imgs.grid">
            <v-card
              v-for="(item,i) in itemsCity"
              :key="i"
              link
              :ripple="{ center: true }"
            >
              <v-row>
                <v-col>
                  <ImageContent :content="item" />
                </v-col>
              </v-row>
            </v-card>
          </div>
        </v-col>
      </transition-group>
    </v-row>
    <div v-if="!showTop">
      <a href="/" class="btn-circle-border-double">TOP</a>
      <!--
      <a href="/">
        <button>TOP</button>
      </a>
-->
    </div>
  </v-container>
</template>
<script>
// 画像一覧表示コンポーネント
import ImageContent from '~/components/ImageContent'

import imageTop from '~/assets/imageTop.json'
import imageGrid from '~/assets/imageGrid.json'

export default {
  components: {
    // コンポーネント定義
    // ImageTopContent,
    ImageContent
  },
  transitions: {
    name: 'fade'
  },
  data () {
    return {
      // TOP画面表示フラグ
      showTop: true,
      // 一覧画面表示情報
      itemsCity: [{}],
      // 画像情報設定
      itemsImage: imageTop,
      // 画像情報設定
      itemsGrid: imageGrid
    }
  },
  methods: {
    showGridArea (id) {
      // TOP画面表示フラグOFF(TOP画像がクリックされたので、OFFにする)
      this.showTop = false
      // 画像情報一時保存用
      const items = []
      // 一覧画面表示判定
      this.itemsImage.forEach(function (images) {
        if (id === images.city) {
        // 一覧画面表示フラグON
          images.grid = true
        } else {
          // 一覧画面表示フラグOFF
          images.grid = false
        }
      })
      // 一覧表示画像情報取得設定
      this.itemsGrid.forEach(function (images) {
        if (id === images.city) {
          // forEach文内でのthisは、繰り返す配列のことを指してしまうので、直接格納することができない
          // 一時保存用の配列へ
          items.push(images)
        }
      })
      // 一時保存したものを一覧画像情報用配列へ
      this.itemsCity = items
    }
  }
}
</script>
<style>
/* 画面カバー文字表示スタイル設定 */
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: .5;
  position: absolute;
  width: 100%;
  writing-mode: vertical-rl;
  text-orientation: upright;
  height: 100%;
}
.v-card--reveal-novertical {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: .5;
  position: absolute;
  width: 100%;
  text-orientation: upright; /* テキストの向き */
  height: 100%;
}
/*
.black {
  color:black;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
*/

button{
  background:orange;
  color:#fff;
  border:none;
  position: fixed;
  bottom: 20px;
  right:10px;
  height:60px;
  font-size:1.6em;
  padding:0 2em;
  cursor:pointer;
  transition:800ms ease all;
  outline:none;
}
button:hover{
  background:#fff;
  color:orange;
}
button:before,button:after{
  content:'';
  position:absolute;
  top:0;
  right:0;
  height:2px;
  width:0;
  background: orange;
  transition:400ms ease all;
}
button:after{
  right:inherit;
  top:inherit;
  left:0;
  bottom:0;
}
button:hover:before,button:hover:after{
  width:100%;
  transition:800ms ease all;
}

/* TOPボタン */
.btn-circle-border-double {
  position: fixed;            /* ボタンを固定 */
  bottom: 10px;               /* 固定位置 */
  right: 30px;                /* 固定位置 */
  display: inline-block;
  text-decoration: none;
  background-color: #fff;   /* 背景色 */
  color: #000000;
  width: 150px;               /* ボタンサイズ横 */
  height: 150px;              /* ボタンサイ縦 */
  line-height: 120px;         /* 行ボックスの高さ */
  border-radius: 50%;         /* 角を取る */
  border: double 10px #000000;  /* 線の種類、太さ、色 */
  font-size: 30px;            /* 文字サイズ */
  text-align: center;         /* 文字表示位置 */
  overflow: hidden;           /* ボックスからはみ出た部分の表示 */
  transition: .6s;
}

a.btn-circle-border-double  {
  color:#000;
}

/* TOPボタンhover時 */
.btn-circle-border-double:hover {
  -webkit-transform: rotateY(360deg);
  transform: rotateY(360deg); /* Y軸を軸とする角度によって時計回りの回転を指定 */
}
</style>
