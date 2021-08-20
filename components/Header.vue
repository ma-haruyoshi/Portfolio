<template>
  <div>
    <v-app-bar
      app
      light
    >
      <v-spacer /> <!-- ボタンを右寄せする -->
      <a v-scroll-to="'#home'" href="#">
        <v-btn text large class="font-weight-regular">
          <v-icon left>
            iconHome
          </v-icon>
        </v-btn>
      </a>
      <a v-scroll-to="'#about'" href="#">
        <v-btn text large class="font-weight-regular">
          <v-icon left>
            iconAccount
          </v-icon>
        </v-btn>
      </a>
      <a v-scroll-to="'#skills'" href="#">
        <v-btn text large class="font-weight-regular">
          <v-icon left>
            mdiDesktopClassic
          </v-icon>
        </v-btn>
      </a>
      <a v-scroll-to="'#gallaly'" href="#">
        <v-btn text large class="font-weight-regular">
          <v-icon left>
            iconCamera
          </v-icon>
        </v-btn>
      </a>
    </v-app-bar>
  </div>
</template>
<script>
import { mdiHome } from '@mdi/js'
import { mdiAccount } from '@mdi/js'
import { mdiDesktopClassic } from '@mdi/js'
import { mdiCamera } from '@mdi/js'
export default {
  data () {
    return {
      iconHome: mdiHome,
      iconAccount: mdiAccount,
      iconDesktopClassic: mdiDesktopClassic,
      iconCamera: mdiCamera
    }
  }
}
</script>
<style>
a {
  text-decoration: none;
}
</style>
