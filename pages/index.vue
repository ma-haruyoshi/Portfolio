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
                    class="d-flex transition-fast-in-fast-out orange darken-2 v-card--reveal display-3 white--text"
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
      <a href="/">
        <button>TOP</button>
      </a>
    </div>
  </v-container>
</template>
<script>
// 画像一覧表示コンポーネント
import ImageContent from '~/components/ImageContent'

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
      itemsImage: [
        {
          city: 'TOKYO',
          src: 'images/tokyotower.jpg',
          grid: false
        },
        {
          city: 'FUKUOKA',
          src: 'images/mojikoutower.jpg',
          grid: false
        },
        {
          city: 'NARA',
          src: 'images/toudaiji.jpg',
          grid: false
        }
      ],
      // 画像情報設定
      itemsGrid: [
        {
          city: 'TOKYO',
          src: 'images/tokyotower.jpg',
          title: '一人タワー',
          author: 'h.maehara',
          description: '初東京タワー。一人で登りました。\r\n東京は高層ビルが多いので、どこでもいい景色な気もしますが、\r\n気分が違う気がしました。\r\n\r\n #おひとり様\r\n #東京タワー \r\n #天気だけはいつも良い \r\n #駅から宿泊ホテル遠すぎた',
          status: false
        },
        {
          city: 'TOKYO',
          src: 'images/tokyo_road.JPG',
          title: '昼間ですが、閑散としていました。',
          author: 'h.maehara',
          description: 'どの辺りかは、忘れました！\r\nあんまり車通ってないなーと思ったような…。\r\n\r\n #おひとり様\r\n #東京タワー \r\n #＼(゜ロ＼)ココハドコ? (／ロ゜)／アタシハダアレ? \r\n #知ってたら教えてください！頷きます！',
          status: false
        },
        {
          city: 'TOKYO',
          src: 'images/tokyo_station.JPG',
          title: '広すぎて迷うので、困ります。',
          author: 'h.maehara',
          description: '滅多に行かないので迷うのですが、攻略できる気はしません。\r\n\r\n#東京駅\r\n#いい運動になる\r\n#フロアマップ迷路\r\n#東京ばな奈は買う',
          status: false
        },
        {
          city: 'TOKYO',
          src: 'images/Mt_Fuji.JPG',
          title: '車窓からにしてはいい感じです。',
          author: 'h.maehara',
          description: '趣味で各地に遠征していたら、\r\nエクスプレス予約のポイント溜まりまくりました。\r\nポイントで帰りはグリーン車で帰岡。\r\n\r\n#新幹線\r\n#富士山\r\n#束の間リッチ\r\n#東京ばな奈は買う',
          status: false
        },
        {
          city: 'FUKUOKA',
          src: 'images/mojikoutower.jpg',
          title: '門司港の高層ビル',
          author: 'h.maehara',
          description: '門司港にあるマンション。\r\n（マンションだったみたいです。知らんかった。）\r\nてっぺんのバケツみたいな気になります。\r\n\r\n #おひとり様 \r\n #門司港タワー \r\n #天気だけはいつも良い \r\n #張り切って早起き',
          status: false
        },
        {
          city: 'FUKUOKA',
          src: 'images/moji_tower.JPG',
          title: '貸し切り展望台',
          author: 'h.maehara',
          description: '偶然にも誰もいませんでした。\r\n海も線路も関門海峡も見放題ですよ！\r\n\r\n #おひとり様\r\n #門司港タワー \r\n #展望室は有料 \r\n #対岸は山口県　\r\n #門司港駅工事中でした',
          status: false
        },
        {
          city: 'FUKUOKA',
          src: 'images/moji_bananaman.JPG',
          title: '思ってたんと違う',
          author: 'h.maehara',
          description: '私の知っているバナナマンじゃなかったです。\r\nでも、バナナ感はこちらの方がありますね。\r\n\r\n #おひとり様\r\n #門司港バナナマン \r\n #バナナの黒い斑点はシュガースポット \r\n #味方ではなく使者 \r\n #ストラップ買いました \r\n #実家の壁に飾ってます',
          status: false
        },
        {
          city: 'FUKUOKA',
          src: 'images/kokura_station.JPG',
          title: '銀河じゃないのに999',
          author: 'h.maehara',
          description: '金髪の謎多き美女がでてくる、\r\n銀河走っちゃう鉄道ですよね。\r\nそれ以上の情報は持ち合わせてないです。\r\nベンチに座って2ショットや3ショットを楽しめますよ。\r\n\r\n #おひとり様\r\n #小倉駅 \r\n #銀河鉄道999 \r\n #目の前はリーガロイヤルホテル',
          status: false
        },
        {
          city: 'FUKUOKA',
          src: 'images/kokurajyo.JPG',
          title: '小倉城',
          author: 'h.maehara',
          description: '桜の季節でいい感じでした。\r\n天守閣にも入場可能です。\r\nそういえば城外でコスプレイヤーが撮影会してました。\r\n忍者は城が似合いますね。\r\n\r\n #おひとり様\r\n #小倉城 \r\n #城内にエレベーターあり \r\n #隣は小倉祇園八坂神社 \r\n #さらに隣はショッピングモール \r\n #付近に観光スポット満載',
          status: false
        },
        {
          city: 'NARA',
          src: 'images/daibutsu.jpg',
          title: '大仏様の手',
          author: 'h.maehara',
          description: '奈良の大仏様の手ですね。\r\n小学校の修学旅行以来でしたが、相変わらず大きい。\r\n小学生の時は、大仏様の鼻の穴サイズの柱の穴を嬉々としてくぐっていました。\r\nくぐるとご利益ある説もあるみたいです。\r\n\r\n #おひとり様 \r\n #東大寺 \r\n #天気だけはいつも良い \r\n #今回、柱の穴くぐりは遠慮',
          status: false
        },
        {
          city: 'NARA',
          src: 'images/kashihara.JPG',
          title: '橿原神宮前',
          author: 'h.maehara',
          description: '橿原ってここに行って読めるようになりました。\r\n平日だったので、ゆったりと参拝できました。\r\n当日、宝物館がお休みでがっかりしました。（下調べ不足）\r\n\r\n #おひとり様\r\n #橿原神宮 \r\n #日本建国の地 \r\n #神武天皇',
          status: false
        },
        {
          city: 'NARA',
          src: 'images/kashihara2.JPG',
          title: '橿原神宮鳥居',
          author: 'h.maehara',
          description: '木製の鳥居が珍しいなと思いました。\r\n参道では骨董市が開かれていたような記憶が。\r\n\r\n #おひとり様\r\n #橿原神宮 \r\n #鳥居 \r\n #駅から近い',
          status: false
        },
        {
          city: 'NARA',
          src: 'images/kashihara3.JPG',
          title: '外拝殿の周り',
          author: 'h.maehara',
          description: 'とにかく厳かな空間でした。\r\n荒んだ心も清らかに解毒されそうです。\r\n何かのアニメの聖地のようで、休憩所にパネルが立ってました。\r\n\r\n #おひとり様\r\n #橿原神宮 \r\n #アニメ聖地 \r\n #デトックス',
          status: false
        },
        {
          city: 'NARA',
          src: 'images/kasugataisya.JPG',
          title: '鹿せんべいたべる？',
          author: 'h.maehara',
          description: '奈良といえば、鹿ですね。\r\n実物はちょっと怖いです。\r\n糞を踏まないように下を見ながら慎重に歩くようにしてました。\r\nが、途中からどうでもよくなり、気にするのをやめました。\r\n\r\n #おひとり様\r\n #春日大社 \r\n #鹿 \r\n #せんとくん と まんとくん \r\n #可愛さなら、まんとくん推し \r\n #インパクトなら、せんとくん推し',
          status: false
        }
      ]
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
.orange {
  color:orange;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

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
</style>
