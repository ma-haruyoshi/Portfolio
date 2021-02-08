<template>
  <v-container class="white" style="margin: 100px auto auto;">
    <div v-if="showTop">
      <v-row no-gutters justify="center">
        <!-- TOP画面 -->
        <v-col v-for="imgs in itemsImage" :key="imgs.city">
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
                    class="d-flex transition-fast-in-fast-out black darken-2 v-card--reveal display-1 white--text"
                  >
                    {{ imgs.city }}
                  </div>
                </v-expand-transition>
              </v-img>
            </v-card>
          </v-hover>
        </v-col>
      </v-row>
    </div>
    <div v-if="!showTop" >
      <v-row no-gutters justify="center">
        <transition-group name="fade" tag="div" class="itemlist">
          <v-col v-for="imgs in itemsImage" :key="imgs.city">
            <div v-if="imgs.grid" >
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
<!--      <div class="bttn-flex">-->
        <a href="/" class="bttn">TOP</a>
<!--      </div>-->
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

*,
*::before,
*::after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

a.bttn {
  color: #000000;
  display: inline-block;
  text-decoration: none;
  transition: 0.3s all ease;
}
a.bttn:hover {
  color: #B15947;
}
a.bttn:focus {
  color: #000000;
}
a.bttn:active {
  color: #FFF;
}

.bttn-flex {
  min-height: 10vh;
  display: flex;
  align-items: center ;
  justify-content: center;
}

.bttn {
  text-align: center;
  width: 50px;
  height: 50px;
  line-height: 50px;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
  font-size: 12px;
  position: fixed;
  bottom:20px;
  right:30px;
}
.bttn:after {
  text-align: center;
  width: 50px;
  height: 50px;
  line-height: 50px;
  transition: 0.3s all ease;
  content: "";
  position: fixed;
/*
  left: 0;
  top: 0;
*/
  bottom: 20px;
  right: 30px;
  border-radius: 3px;
  border: 3px solid #B15947;
}
.bttn:before {
  text-align: center;
  width: 50px;
  height: 50px;
  line-height: 50px;
  content: "";
  position: fixed;
  border-radius: 3px;
  background-color: #fff;
/*
  border: 3px solid #B15947;
  left: 0;
  top: 0;
*/
  bottom: 20px;
  right: 30px;
  -webkit-transform: rotate(45deg);
  transform: rotate(45deg);
  z-index: -1;
}
.bttn:hover:after {
  -webkit-transform: rotate(45deg);
  transform: rotate(45deg);
}
/*
.bttn:active {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
.bttn:active:before {
  background-color: #fff;
}
.bttn:active:after {
  border-color: #f1481b;
}
*/
.itemlist {
  min-width: 300px;
  max-width: 750px;
  width: 100%;
}
</style>
