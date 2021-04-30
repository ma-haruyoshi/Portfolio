<template>
  <div>
    <div
      v-for="(data,i) in item"
      :key="i"
    >
      <v-row>
        <v-col>
          <v-card
            flat
            tile
            class="mx-auto"
          >
            <v-progress-circular
              :rotate="-90"
              :size="100"
              :width="7"
              :value="value"
              :color="data.color"
            >
              {{ data.lang }}
            </v-progress-circular>
            <v-card-actions class="white">
              <v-spacer />
              もっと見る
              <v-btn
                icon
                @click="data.show = !data.show"
              >
                <v-icon>{{ data.show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
              </v-btn>
            </v-card-actions>
            <v-expand-transition>
              <div v-show="data.show" class="white">
                <!-- 区切り線 -->
                <v-divider />
                <!-- 本文 -->
                <v-card-text class="text-left">
                  {{ data.text }}
                </v-card-text>
              </div>
            </v-expand-transition>
          </v-card>
        </v-col>
      </v-row>
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
      interval: {},
      value: 0,
      full: false,
      // 呼び出し元のデータを変更することができないため、コンポーネントで扱うためのオブジェクト定義
      item: null
    }
  },
  beforeDestroy () {
    clearInterval(this.interval)
  },
  mounted () {
    // コンポーネントで扱うオブジェクトへ渡されてきたオブジェクトをセット
    this.item = this.content
    // プログレスバー動作設定
    this.interval = setInterval(() => {
      if (this.value === 100) {
        this.full = true
      } else if (this.value === 0) {
        this.full = false
      }
      if (this.full) {
        this.value -= 20
      } else {
        this.value += 20
      }
    }, 1000)
  }
}
</script>

<style>
.v-progress-circular {
  margin: 1rem;
}
.white {
  background-color: white;
  white-space: pre-line;
  word-wrap: break-word;
}
</style>
