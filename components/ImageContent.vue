<template>
  <div>
    <div class="space" />
    <div class="gallery3d">
      <div id="carousel">
        <figure
          v-for="(slide,i) in item"
          id="round"
          :key="i"
        >
          <v-dialog light content-class="v-dialog-style">
            <template #activator="{ on }">
              <v-img :src="slide.src" v-on="on" />
            </template>
            <v-card flat tile>
              <!-- タイトル -->
              <v-card-title class="body-2 black--text">
                {{ slide.title }}
              </v-card-title>
              <v-img :src="slide.src" max-height="450" contain />
              <!-- 本文 -->
              <v-card-text class="item-description caption black--text">
                {{ slide.description }}
              </v-card-text>
            </v-card>
          </v-dialog>
        </figure>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    // 呼び出し元から渡されるオブジェクト(画像一覧情報)
    content: {
      type: Array
    }
  },
  data () {
    return {
      // 呼び出し元のデータを変更することができないため、コンポーネントで扱うためのオブジェクト定義
      item: null
    }
  },
  mounted () {
    // コンポーネントで扱うオブジェクトへ渡されてきたオブジェクトをセット
    this.item = this.content
  }
}
</script>
<style>
.item-description {
  text-align: left;
  white-space: pre-line;
  word-wrap: break-word;
}
.v-dialog-style {
  max-width:500px;
}
/* スクロールの幅の設定 */
.v-dialog-style::-webkit-scrollbar {
 width: 10px;
 height: 10px;
}

/* スクロールの背景の設定 */
.v-dialog-style::-webkit-scrollbar-track {
 border-radius: 5px;
 background: #707070;
}

/* ドラックできるスクロール部の設定 */
.v-dialog-style::-webkit-scrollbar-thumb {
 border-radius: 5px;
 background: rgba(255, 255, 255, 0.7); /* 4番目の値で色の透明度を調節 */
}
.v-card-style {
  max-width:500px;
  height:100%;
  background-color: black !important;
  color: white !important;
}
.v-card--reveal {
  align-items: center;
  top: 0;
  justify-content: center;
  opacity: .6;
  position: absolute;
  width: 100%;
  height: 100%;
}
.v-img-style {
  opacity: .6;
}
.gallery3d{
  margin: 4% auto;
  width: 210px;
  height: 140px;
  position: relative;
  perspective: 1000px;
}
#carousel{
  width: 100%;
  height: 100%;
  position: absolute;
  transform-style: preserve-3d;
  animation: rotation 20s infinite linear;
}
#carousel:hover{
  animation-play-state: paused;
}
#carousel figure{
  display: block;
  position: absolute;
  width: 125px;
  /* height: 116px;*/
  left: 10px;
  top: 10px;
  background: black;
  overflow: hidden;
  /* border: solid 5px black; */
}
/* 写真がぐるぐる動いている箇所の設定 */
#carousel figure:nth-child(1){transform: rotateY(0deg) translateZ(288px);}
#carousel figure:nth-child(2) { transform: rotateY(25deg) translateZ(288px);}
#carousel figure:nth-child(3) { transform: rotateY(50deg) translateZ(288px);}
#carousel figure:nth-child(4) { transform: rotateY(75deg) translateZ(288px);}
#carousel figure:nth-child(5) { transform: rotateY(100deg) translateZ(288px);}
#carousel figure:nth-child(6) { transform: rotateY(125deg) translateZ(288px);}
#carousel figure:nth-child(7) { transform: rotateY(150deg) translateZ(288px);}
#carousel figure:nth-child(8) { transform: rotateY(175deg) translateZ(288px);}
#carousel figure:nth-child(9) { transform: rotateY(200deg) translateZ(288px);}
#carousel figure:nth-child(10) { transform: rotateY(225deg) translateZ(288px);}
#carousel figure:nth-child(11) { transform: rotateY(250deg) translateZ(288px);}
#carousel figure:nth-child(12) { transform: rotateY(275deg) translateZ(288px);}
#carousel figure:nth-child(13) { transform: rotateY(300deg) translateZ(288px);}
#carousel figure:nth-child(14) { transform: rotateY(325deg) translateZ(288px);}

img{
  -webkit-filter: grayscale(1);
  cursor: pointer;
  transition: all .5s ease;
  width: 100%;
  height: auto;
}
img:hover{
  -webkit-filter: grayscale(0);
  transform: scale(1.2,1.2);
}

@keyframes rotation{
  from{
    transform: rotateY(0deg);
  }
  to{
    transform: rotateY(360deg);
  }
}
</style>
