<template>
  <div class="text-center">
    <v-progress-circular
      :rotate="-90"
      :size="100"
      :width="7"
      :value="value"
      color="blue-grey"
    >
      Cold Fusion
    </v-progress-circular>
    <p>入社したての頃、頭を悩ませた</p>

    <v-progress-circular
      :rotate="-90"
      :size="100"
      :width="7"
      :value="value"
      color="deep-orange lighten-2"
    >
      Java
    </v-progress-circular>
    <p>入社から数年後、頭を悩ませた</p>

    <v-progress-circular
      :rotate="-90"
      :size="100"
      :width="7"
      :value="value"
      color="indigo darken-2"
    >
      VBA
    </v-progress-circular>
    <p>入社からさらに数年後、頭を悩ませた</p>

    <v-progress-circular
      :rotate="-90"
      :size="100"
      :width="7"
      :value="value"
      color="brown"
    >
      PHP
    </v-progress-circular>
    <p>今から数年前、頭を悩ませた</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      interval: {},
      value: 0
    }
  },
  beforeDestroy () {
    clearInterval(this.interval)
  },
  mounted () {
    this.interval = setInterval(() => {
      if (this.value === 100) {
        return (this.value = 0)
      }
      this.value += 20
    }, 1000)
  }
}
</script>

<style scoped>
.v-progress-circular {
  margin: 1rem;
}
</style>
