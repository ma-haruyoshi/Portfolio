<template>
  <!-- 画像情報が空で無い場合のみ表示処理実行 -->
  <div v-if="item" @click="showTitleArea()">
    <!-- 各画像がクリックされた場合 -->
    <div v-if="item.status">
      <v-row>
        <!-- 左に画像表示 -->
        <v-col cols="5">
          <v-img
            :src="item.src"
            class="item-display-left"
          />
        </v-col>
        <!-- 右に概要表示 -->
        <v-col>
          <v-list-item>
            <!-- 丸いところ -->
            <v-list-item-avatar color="grey" />
            <v-list-item-content>
              <!-- タイトル -->
              <v-list-item-title class="body-1">
                {{ item.title }}
              </v-list-item-title>
              <!-- 撮影者 -->
              <v-list-item-subtitle class="caption">
                {{ item.author }}
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <!-- 説明（改行は、改行コードでできる） -->
          <div class="item-description body-2">
            {{ item.description }}
          </div>
        </v-col>
      </v-row>
    </div>
    <!-- 各画像がクリックされていない、初期表示 -->
    <div v-else>
      <v-hover v-slot:default="{ hover }">
        <div>
          <!-- 横長で画像表示 -->
          <v-img
            :src="item.src"
            class="itemlist-display"
          >
            <v-expand-transition>
              <div
                v-if="!hover"
                class="d-flex transition-ease-in-out black darken-2 v-card--reveal-novertical"
              />
            </v-expand-transition>
          </v-img>
        </div>
      </v-hover>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    // 呼び出し元から渡されるオブジェクト(画像一覧情報)
    content: {
      type: Object
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
  },
  methods: {
    // 一覧画像選択時の処理
    showTitleArea () {
      // 画像情報ステータス変更(クリック毎にstatus値を反転)
      this.item.status = !this.item.status
    }
  }
}
</script>

<style>
.itemlist-display {
  /* 左右余白 */
  margin: 0px 10px 0px 10px;
  height: 150px;
  object-fit: cover;
}
.item-display-left {
  /* 左余白 */
  margin: 0px 0px 0px 10px;
  max-width: 300px;
  object-fit: fill;
}
.item-description {
  white-space: pre-line;
  word-wrap: break-word;
}
</style>
