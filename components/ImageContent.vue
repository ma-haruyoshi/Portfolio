<template>
  <v-hover v-slot:default="{ hover }">
    <v-carousel :show-arrows="true" hide-delimiters style="max-width:350px;">
      <v-carousel-item
        v-for="(slide,i) in item"
        :key="i"
        :src="slide.src"
      >
        <v-expand-transition>
          <div
            v-if="hover"
            class="transition-fast-in-fast-out black v-card--reveal"
          >
            <v-card class="v-card-style" flat tile>
              <v-card-title class="body-2 white--text">
                {{ slide.title }}
              </v-card-title>
              <v-card-text class="item-description caption white--text">
                {{ slide.description }}
              </v-card-text>
            </v-card>
          </div>
        </v-expand-transition>
      </v-carousel-item>
    </v-carousel>
  </v-hover>
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
  position: absolute;
  bottom: 0;
  white-space: pre-line;
  word-wrap: break-word;
}
.slide-block {
  max-width:750px;
}
.v-card-style {
  max-width:750px;
  height:100%;
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
</style>
