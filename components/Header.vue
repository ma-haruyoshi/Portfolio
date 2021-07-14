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
            mdi-home
          </v-icon>
        </v-btn>
      </a>
      <a v-scroll-to="'#about'" href="#">
        <v-btn text large class="font-weight-regular">
          <v-icon left>
            mdi-account
          </v-icon>
        </v-btn>
      </a>
      <a v-scroll-to="'#skills'" href="#">
        <v-btn text large class="font-weight-regular">
          <v-icon left>
            mdi-desktop-classic
          </v-icon>
        </v-btn>
      </a>
      <a v-scroll-to="'#gallaly'" href="#">
        <v-btn text large class="font-weight-regular">
          <v-icon left>
            mdi-camera
          </v-icon>
        </v-btn>
      </a>
    </v-app-bar>
  </div>
</template>
<style>
a {
  text-decoration: none;
}
</style>
