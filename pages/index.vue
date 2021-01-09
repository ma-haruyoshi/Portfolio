<template>
  <v-container class="white">
    <v-row no-gutters justify="center">
      <v-hover v-slot:default="{ hover }">
        <!-- TOP画面 -->
        <v-col v-if="tokyoShow">
          <v-card
            class="mx-auto"
            color="white"
            @click="showGridArea('tokyo')"
          >
            <v-img
              :aspect-ratio="9/16"
              src="images/tokyotower.jpg"
            >
              <v-expand-transition>
                <!-- TOP画面の画像カバー文字出現 -->
                <div
                  v-if="hover && !tokyoGrid"
                  class="d-flex transition-fast-in-fast-out orange darken-2 v-card--reveal display-3 white--text"
                  style="writing-mode: vertical-rl; text-orientation: upright; height: 100%;"
                >
                  TOKYO
                </div>
              </v-expand-transition>
            </v-img>
          </v-card>
        </v-col>
      </v-hover>
      <!-- いい感じで次画面をふわっと表示 -->
      <transition name="fade">
        <!-- 画像一覧表示 -->
        <v-col v-if="tokyoGrid">
          <!-- 画像情報をループして表示 -->
          <v-card
            v-for="(item,i) in itemsTokyo"
            :key="i"
            link
            :ripple="{ center: true }"
            @click="showTitleArea(i,'tokyo')"
          >
            <v-row>
              <v-col>
                <div v-if="item.status">
                  <!-- 各画像がクリックされた場合 -->
                  <v-row>
                    <!-- 左に画像表示 -->
                    <v-col cols="6">
                      <v-img
                        :src="item.src"
                        height="100%"
                      />
                    </v-col>
                    <!-- 右に概要表示 -->
                    <v-col>
                      <v-list-item>
                        <!-- 丸いところ -->
                        <v-list-item-avatar color="grey" />
                        <v-list-item-content>
                          <!-- タイトル -->
                          <v-list-item-title class="display-1">
                            {{ item.title }}
                          </v-list-item-title>
                          <!-- 撮影者 -->
                          <v-list-item-subtitle class="headline">
                            {{ item.author }}
                          </v-list-item-subtitle>
                        </v-list-item-content>
                      </v-list-item>
                      <!-- 説明（改行は、改行コードでできる） -->
                      <div style="font-size: x-large; white-space:pre-wrap; word-wrap:break-word;">{{ item.description }}</div>
                    </v-col>
                  </v-row>
                </div>
                <!-- 各画像がクリックされていない、初期表示 -->
                <div v-else>
                  <!-- 横長で画像表示 -->
                  <v-img
                    :src="item.src"
                    height="400"
                  />
                </div>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </transition>
      <v-hover v-slot:default="{ hover }">
        <!-- TOP画面 -->
        <v-col v-if="fukuokaShow">
          <v-card
            class="mx-auto"
            color="white"
            @click="showGridArea('fukuoka')"
          >
            <v-img
              :aspect-ratio="9/16"
              src="images/mojikoutower.jpg"
            >
              <v-expand-transition>
                <!-- TOP画面の画像カバー文字出現 -->
                <div
                  v-if="hover && !fukuokaGrid"
                  class="d-flex transition-fast-in-fast-out orange darken-2 v-card--reveal display-3 white--text"
                  style="writing-mode: vertical-rl; text-orientation: upright; height: 100%;"
                >
                  FUKUOKA
                </div>
              </v-expand-transition>
            </v-img>
          </v-card>
        </v-col>
      </v-hover>
      <!-- いい感じで次画面をふわっと表示 -->
      <transition name="fade">
        <!-- 画像一覧表示 -->
        <v-col v-if="fukuokaGrid">
          <!-- 画像情報をループして表示 -->
          <v-card
            v-for="(item,i) in itemsFukuoka"
            :key="i"
            link
            :ripple="{ center: true }"
            @click="showTitleArea(i,'fukuoka')"
          >
            <v-row>
              <v-col>
                <div v-if="item.status">
                  <!-- 各画像がクリックされた場合 -->
                  <v-row>
                    <!-- 左に画像表示 -->
                    <v-col cols="6">
                      <v-img
                        :src="item.src"
                        height="100%"
                      />
                    </v-col>
                    <!-- 右に概要表示 -->
                    <v-col>
                      <v-list-item>
                        <!-- 丸いところ -->
                        <v-list-item-avatar color="grey" />
                        <v-list-item-content>
                          <!-- タイトル -->
                          <v-list-item-title class="display-1">
                            {{ item.title }}
                          </v-list-item-title>
                          <!-- 撮影者 -->
                          <v-list-item-subtitle class="headline">
                            {{ item.author }}
                          </v-list-item-subtitle>
                        </v-list-item-content>
                      </v-list-item>
                      <!-- 説明（改行は、改行コードでできる） -->
                      <div style="font-size: x-large; white-space:pre-wrap; word-wrap:break-word;">{{ item.description }}</div>
                    </v-col>
                  </v-row>
                </div>
                <!-- 各画像がクリックされていない、初期表示 -->
                <div v-else>
                  <!-- 横長で画像表示 -->
                  <v-img
                    :src="item.src"
                    height="400"
                  />
                </div>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </transition>
      <v-hover v-slot:default="{ hover }">
        <!-- TOP画面 -->
        <v-col v-if="naraShow">
          <v-card
            class="mx-auto"
            color="white"
            @click="showGridArea('nara')"
          >
            <v-img
              :aspect-ratio="9/16"
              src="images/toudaiji.jpg"
            >
              <v-expand-transition>
                <!-- TOP画面の画像カバー文字出現 -->
                <div
                  v-if="hover && !naraGrid"
                  class="d-flex transition-fast-in-fast-out orange darken-2 v-card--reveal display-3 white--text"
                  style="writing-mode: vertical-rl; text-orientation: upright; height: 100%;"
                >
                  NARA
                </div>
              </v-expand-transition>
            </v-img>
          </v-card>
        </v-col>
      </v-hover>
      <!-- いい感じで次画面をふわっと表示 -->
      <transition name="fade">
        <!-- 画像一覧表示 -->
        <v-col v-if="naraGrid">
          <!-- 画像情報をループして表示 -->
          <v-card
            v-for="(item,i) in itemsNara"
            :key="i"
            link
            :ripple="{ center: true }"
            @click="showTitleArea(i,'nara')"
          >
            <v-row>
              <v-col>
                <div v-if="item.status">
                  <!-- 各画像がクリックされた場合 -->
                  <v-row>
                    <!-- 左に画像表示 -->
                    <v-col cols="6">
                      <v-img
                        :src="item.src"
                        height="100%"
                      />
                    </v-col>
                    <!-- 右に概要表示 -->
                    <v-col>
                      <v-list-item>
                        <!-- 丸いところ -->
                        <v-list-item-avatar color="grey" />
                        <v-list-item-content>
                          <!-- タイトル -->
                          <v-list-item-title class="display-1">
                            {{ item.title }}
                          </v-list-item-title>
                          <!-- 撮影者 -->
                          <v-list-item-subtitle class="headline">
                            {{ item.author }}
                          </v-list-item-subtitle>
                        </v-list-item-content>
                      </v-list-item>
                      <!-- 説明（改行は、改行コードでできる） -->
                      <div style="font-size: x-large; white-space:pre-wrap; word-wrap:break-word;">{{ item.description }}</div>
                    </v-col>
                  </v-row>
                </div>
                <!-- 各画像がクリックされていない、初期表示 -->
                <div v-else>
                  <!-- 横長で画像表示 -->
                  <v-img
                    :src="item.src"
                    height="400"
                  />
                </div>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </transition>
    </v-row>
  </v-container>
</template>
<script>
export default {
  transitions: {
    name: 'fade'
  },
  data () {
    return {
      // TOKYO TOP画像表示フラグ
      tokyoShow: true,
      // TOKYO 一覧画面表示フラグ
      tokyoGrid: false,
      // FUKUOKA TOP画像表示フラグ
      fukuokaShow: true,
      // FUKUOKA 一覧画面表示フラグ
      fukuokaGrid: false,
      // NARA TOP画像表示フラグ
      naraShow: true,
      // NARA 一覧画面表示フラグ
      naraGrid: false,
      items: [{}],
      // 画像情報設定
      itemsTokyo: [
        {
          src: 'images/tokyotower.jpg',
          title: '一人タワー',
          author: 'h.maehara',
          description: '初東京タワー。一人で登りました。\r\n東京は高層ビルが多いので、どこでもいい景色な気もしますが、\r\n気分が違う気がしました。\r\n\r\n #おひとり様\r\n #東京タワー \r\n #天気だけはいつも良い \r\n #駅から宿泊ホテル遠すぎた',
          status: false
        },
        {
          src: 'images/tokyo_road.JPG',
          title: '昼間ですが、閑散としていました。',
          author: 'h.maehara',
          description: 'どの辺りかは、忘れました！\r\nあんまり車通ってないなーと思ったような…。\r\n\r\n #おひとり様\r\n #東京タワー \r\n #＼(゜ロ＼)ココハドコ? (／ロ゜)／アタシハダアレ? \r\n #知ってたら教えてください！頷きます！',
          status: false
        },
        {
          src: 'images/tokyo_station.JPG',
          title: '広すぎて迷うので、困ります。',
          author: 'h.maehara',
          description: '滅多に行かないので迷うのですが、攻略できる気はしません。\r\n\r\n#東京駅\r\n#いい運動になる\r\n#フロアマップ迷路\r\n#東京ばな奈は買う',
          status: false
        },
        {
          src: 'images/Mt_Fuji.JPG',
          title: '車窓からにしてはいい感じです。',
          author: 'h.maehara',
          description: '趣味で各地に遠征していたら、\r\nエクスプレス予約のポイント溜まりまくりました。\r\nポイントで帰りはグリーン車で帰岡。\r\n\r\n#新幹線\r\n#富士山\r\n#束の間リッチ\r\n#東京ばな奈は買う',
          status: false
        }
      ],
      itemsFukuoka: [
        {
          src: 'images/mojikoutower.jpg',
          title: '門司港の高層ビル',
          author: 'h.maehara',
          description: '門司港にあるマンション。\r\n（マンションだったみたいです。知らんかった。）\r\nてっぺんのバケツみたいな気になります。\r\n\r\n #おひとり様 \r\n #門司港タワー \r\n #天気だけはいつも良い \r\n #張り切って早起き',
          status: false
        },
        {
          src: 'images/moji_tower.JPG',
          title: '貸し切り展望台',
          author: 'h.maehara',
          description: '偶然にも誰もいませんでした。\r\n海も線路も関門海峡も見放題ですよ！\r\n\r\n #おひとり様\r\n #門司港タワー \r\n #展望室は有料 \r\n #対岸は山口県　\r\n #門司港駅工事中でした',
          status: false
        },
        {
          src: 'images/moji_bananaman.JPG',
          title: '思ってたんと違う',
          author: 'h.maehara',
          description: '私の知っているバナナマンじゃなかったです。\r\nでも、バナナ感はこちらの方がありますね。\r\n\r\n #おひとり様\r\n #門司港バナナマン \r\n #バナナの黒い斑点はシュガースポット \r\n #味方ではなく使者 \r\n #ストラップ買いました \r\n #実家の壁に飾ってます',
          status: false
        },
        {
          src: 'images/kokura_station.JPG',
          title: '銀河じゃないのに999',
          author: 'h.maehara',
          description: '金髪の謎多き美女がでてくる、\r\n銀河走っちゃう鉄道ですよね。\r\nそれ以上の情報は持ち合わせてないです。\r\nベンチに座って2ショットや3ショットを楽しめますよ。\r\n\r\n #おひとり様\r\n #小倉駅 \r\n #銀河鉄道999 \r\n #目の前はリーガロイヤルホテル',
          status: false
        },
        {
          src: 'images/kokurajyo.JPG',
          title: '小倉城',
          author: 'h.maehara',
          description: '桜の季節でいい感じでした。\r\n天守閣にも入場可能です。\r\nそういえば城外でコスプレイヤーが撮影会してました。\r\n忍者は城が似合いますね。\r\n\r\n #おひとり様\r\n #小倉城 \r\n #城内にエレベーターあり \r\n #隣は小倉祇園八坂神社 \r\n #さらに隣はショッピングモール \r\n #付近に観光スポット満載',
          status: false
        }
      ],
      itemsNara: [
        {
          src: 'images/daibutsu.jpg',
          title: '大仏様の手',
          author: 'h.maehara',
          description: '奈良の大仏様の手ですね。\r\n小学校の修学旅行以来でしたが、相変わらず大きい。\r\n小学生の時は、大仏様の鼻の穴サイズの柱の穴を嬉々としてくぐっていました。\r\nくぐるとご利益ある説もあるみたいです。\r\n\r\n #おひとり様 \r\n #東大寺 \r\n #天気だけはいつも良い \r\n #今回、柱の穴くぐりは遠慮',
          status: false
        },
        {
          src: 'images/kashihara.JPG',
          title: '橿原神宮前',
          author: 'h.maehara',
          description: '橿原ってここに行って読めるようになりました。\r\n平日だったので、ゆったりと参拝できました。\r\n当日、宝物館がお休みでがっかりしました。（下調べ不足）\r\n\r\n #おひとり様\r\n #橿原神宮 \r\n #日本建国の地 \r\n #神武天皇',
          status: false
        },
        {
          src: 'images/kashihara2.JPG',
          title: '橿原神宮鳥居',
          author: 'h.maehara',
          description: '木製の鳥居が珍しいなと思いました。\r\n参道では骨董市が開かれていたような記憶が。\r\n\r\n #おひとり様\r\n #橿原神宮 \r\n #鳥居 \r\n #駅から近い',
          status: false
        },
        {
          src: 'images/kashihara3.JPG',
          title: '外拝殿の周り',
          author: 'h.maehara',
          description: 'とにかく厳かな空間でした。\r\n荒んだ心も清らかに解毒されそうです。\r\n何かのアニメの聖地のようで、休憩所にパネルが立ってました。\r\n\r\n #おひとり様\r\n #橿原神宮 \r\n #アニメ聖地 \r\n #デトックス',
          status: false
        },
        {
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
    // 一覧画面表示フラグ設定
    showGridArea (id) {
      if (id === 'tokyo') {
        this.tokyoShow = false
        this.tokyoGrid = true
        this.fukuokaShow = false
        this.fukuokaGrid = false
        this.naraShow = false
        this.naraGrid = false
      } else if (id === 'fukuoka') {
        this.fukuokaShow = false
        this.fukuokaGrid = true
        this.tokyoShow = false
        this.tokyoGrid = false
        this.naraShow = false
        this.naraGrid = false
      } else if (id === 'nara') {
        this.naraShow = false
        this.naraGrid = true
        this.tokyoShow = false
        this.tokyoGrid = false
        this.fukuokaShow = false
        this.fukuokaGrid = false
      }
    },
    // 一覧画像選択時の処理
    showTitleArea (idx, id) {
      // 一覧画像情報初期化
      this.items = []
      // 各一覧画像情報設定
      if (id === 'tokyo') {
        this.items = this.itemsTokyo
      } else if (id === 'fukuoka') {
        this.items = this.itemsFukuoka
      } else if (id === 'nara') {
        this.items = this.itemsNara
      }
      // 画像情報ステータス変更
      if (this.items[idx].status === false) {
        // 画像詳細表示OFF状態から画像選択、ステータスON
        this.items[idx].status = true
      } else {
        // 画像詳細表示ON状態から画像選択、ステータスOFF
        this.items[idx].status = false
      }
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
</style>
