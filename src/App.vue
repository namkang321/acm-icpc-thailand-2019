<template>
  <v-app v-scroll="onScroll">
    <v-toolbar :color="colorByScroll" fixed flat>
      <router-link
        to="/"
        tag="img"
        height="70%"
        contain
        position="left"
        :src="logoByScroll"
        :style="{ cursor: 'pointer' }"
      ></router-link>
      <v-spacer></v-spacer>
      <v-toolbar-side-icon
        :style="{ color: hamburgerColor, backgroundColor: hamburgerColorBg }"
        class="hamburger"
        dark
        @click.stop="drawer = !drawer"
      ></v-toolbar-side-icon>
      <v-toolbar-items class="not-hamburger">
        <v-btn :color="colorToolbarTextByScroll" to="/" flat>Home</v-btn>
        <v-btn :color="colorToolbarTextByScroll" to="/contest" flat>Contest</v-btn>
        <v-btn :color="colorToolbarTextByScroll" to="/rules" flat>Rules</v-btn>
        <v-btn :color="colorToolbarTextByScroll" to="/contacts" flat>Contacts & Hosts</v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-parallax :src="red_castle" height="550" style="padding: 0 !important;">
      <div id="main" style="position: absolute; z-index: 6;">
        <div class="px-5 mt-5 pt-5">
          <h1 class="text-shadow text-title">ICPC Regional Contest 2019</h1>
        </div>
        <transition name="slide-fade">
          <div v-if="isVisible" class="px-5 mt-3" style="display: flex;">
            <div>
              <h2 class="text-shadow text-body">
                Online Round:
              </h2>
              <h2 class="text-shadow text-body">
                Register Date: 26 Aug - 07 Oct 2019
              </h2>
              <h2 class="text-shadow text-body">
                Contest Date: 18 Oct 2019
              </h2>
              <v-btn
                large
                round
                depressed
                color="#6b0000"
                dark
                style="margin: 0 !important; margin-top: 10px !important;"
                ref="register_btn"
                href="https://icpc.baylor.edu/regionals/finder/AsiaBankOnline-2019"
                target="_blank"
                class="register_btn-text"
                id="register_btn"
              >
                <span><v-icon class="register_btn-icon">create</v-icon> Online</span>
              </v-btn>
            </div>
            <div class="partition mx-3" />
            <div>
              <h2 class="text-shadow text-body">
                Regional Round:
              </h2>
              <h2 class="text-shadow text-body">
                Register Date: 09 Sep - 07 Oct 2019
              </h2>
              <h2 class="text-shadow text-body">
                Contest Date: 02 Nov - 03 Nov 2019
              </h2>
              <v-btn
                large
                round
                depressed
                color="#6b0000"
                dark
                style="margin: 0 !important; margin-top: 10px !important;"
                href="https://icpc.baylor.edu/regionals/finder/AsiaBangkok-2019"
                target="_blank"
                class="register_btn-text"
              >
                <span><v-icon class="register_btn-icon">create</v-icon> Regional</span>
              </v-btn>
            </div>
          </div>
        </transition>
        <div class="text-xs pt-3 px-5 register"></div>
        <div class="content px-5 mb-2 pt-5"></div>
      </div>
      <div class="shadow" style="z-index: 5;"></div>
    </v-parallax>
    <transition name="fade" mode="out-in" duration="400">
      <router-view :key="$route.fullPath"></router-view>
    </transition>
    <transition name="slide-fade">
      <v-speed-dial
        v-if="show_float_btn"
        v-model="fab"
        :top="top"
        :bottom="bottom"
        :right="right"
        :left="left"
        :direction="direction"
        :open-on-hover="hover"
        :transition="transition"
        fixed
      >
        <template v-slot:activator>
          <v-btn v-model="fab" dark round large color="#6b0000" @click="updateShowFAB">
            <span v-if="!showFAB"><v-icon>create</v-icon> Register</span>
            <v-icon v-if="showFAB">close</v-icon>
          </v-btn>
        </template>
        <v-btn
          round
          color="pink lighten-5"
          href="https://icpc.baylor.edu/regionals/finder/AsiaBankOnline-2019"
          target="_blank"
          style="font-size: 12px; max-width: 56px"
        >
          <span>Online</span>
        </v-btn>
        <v-btn
          round
          color="pink lighten-5"
          href="https://icpc.baylor.edu/regionals/finder/AsiaBangkok-2019"
          target="_blank"
          style="font-size: 12px; max-width: 56px"
        >
          <span>Regional</span>
        </v-btn>
      </v-speed-dial>
    </transition>
    <div class="pt-5 pb-3" id="content-cu-eng">
      <img
        :src="require(`@/assets/cu-eng-logo.png`)"
        alt="Chula Engineering"
        width="50%"
        style="display: block; margin-left: auto; margin-right: auto;"
      />
    </div>
    <v-navigation-drawer
      style="background-color: rgba(107,0,0,0.85); max-width: 75%"
      v-model="drawer"
      fixed
      bottom
      temporary
      right
    >
      <v-list class="pt-0" dense>
        <v-divider light></v-divider>

        <v-list-tile>
          <v-list-tile-content>
            <router-link
              style="text-decoration: none; color: white; font-size: 20px; font-weight:300; padding-top: 20px; padding-left: 20px"
              to="/"
              >Home</router-link
            >
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile>
          <v-list-tile-content>
            <router-link
              style="text-decoration: none; color: white; font-size: 20px; font-weight:300; padding-top: 20px; padding-left: 20px"
              to="/contest"
              >Contest</router-link
            >
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile>
          <v-list-tile-content>
            <router-link
              style="text-decoration: none; color: white; font-size: 20px; font-weight:300; padding-top: 20px; padding-left: 20px"
              to="/rules"
              >Rules</router-link
            >
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile>
          <v-list-tile-content>
            <router-link
              style="text-decoration: none; color: white; font-size: 20px; font-weight:300; padding-top: 20px; padding-left: 20px"
              to="/contacts"
              >Contacts & Hosts</router-link
            >
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
  </v-app>
</template>

<script>
const logo_color = require('@/assets/logo-color.png')
const logo_white = require('@/assets/logo.png')
const red_castle = require('@/assets/red-castle-blur.jpg')
export default {
  data: () => ({
    offsetTop: 0,
    show_float_btn: false,
    logo_color: logo_color,
    logo_white: logo_white,
    red_castle: red_castle,
    isVisible: false,
    drawer: false,
    direction: 'top',
    fab: false,
    fling: false,
    hover: false,
    tabs: null,
    top: false,
    right: true,
    bottom: true,
    left: false,
    transition: 'slide-y-reverse-transition',
    showRegister: false,
    showFAB: false,
    hamburgerColor: '#6b0000',
    hamburgerColorBg: 'rgba(0,0,0,0)'
  }),
  computed: {
    logoByScroll: function() {
      return this.offsetTop == 0 ? this.logo_color : this.logo_white
    },
    colorByScroll: function() {
      return 'rgba(0,0,0,' + this.transparency() + ')'
    },
    colorToolbarTextByScroll: function() {
      return this.offsetTop == 0 ? '#6b0000 !important' : 'white !important'
    }
  },
  methods: {
    updateShowFAB: function() {
      let speedDialList = document.getElementsByClassName('v-speed-dial__list')[0].innerHTML
      if (speedDialList) {
        this.showFAB = false
      } else {
        this.showFAB = true
      }
    },
    showRegisterOptions: function() {
      this.showRegister = !this.showRegister
    },
    transparency: function() {
      if (this.offsetTop > 7) {
        return 0.7
      } else {
        return this.offsetTop / 10
      }
    },
    onScroll(e) {
      this.offsetTop = window.pageYOffset || document.documentElement.scrollTop
      if (this.offsetTop == 0) {
        this.hamburgerColor = '#6b0000'
      } else {
        this.hamburgerColor = 'white'
      }
      var div = this.$refs.register_btn.$el
      if (div) {
        var rect = div.getBoundingClientRect()
        return (this.show_float_btn = rect.bottom <= 0)
      }
      return (this.show_float_btn = false)
    }
  },
  mounted() {
    this.isVisible = !this.isVisible
  },

  name: 'App',
  components: {}
}
</script>

<style>
.v-speed-dial__list {
  pointer-events: auto !important;
}
.v-parallax__content {
  padding-right: 0 !important;
  padding-left: 0 !important;
}
.shadow {
  z-index: 5;
  background-image: linear-gradient(to bottom, transparent 75%, #000000);
  height: 100%;
  widows: 100%;
}
.text-shadow {
  text-shadow: 2px 2px 4px #000000;
  color: white;
}
@media screen and (min-width: 700px) {
  .hamburger {
    display: none !important;
  }
  .not-hamburger {
    display: block !important;
  }
  .register_btn-icon {
    display: inline-flex !important;
  }
}
@media screen and (max-width: 700px) {
  .hamburger {
    display: block !important;
  }
  .not-hamburger {
    display: none !important;
  }
  .register_btn-text {
    max-width: 36px !important;
    font-size: 13px !important;
  }
  .register_btn-icon {
    display: none !important;
  }
}
@media screen and (min-width: 956px) {
  .text-title {
    font-size: 70px;
  }
  .my-display-1 {
    font-size: 36px !important;
    color: #6b0000;
    font-family: Roboto, sans-serif !important;
    letter-spacing: normal !important;
    line-height: 40px !important;
    font-weight: 400;
  }
  h1 {
    font-size: 4rem;
    font-weight: 500;
    color: #6b0000;
    font-family: Roboto, sans-serif !important;
  }
  .partition {
    border: 0;
    width: 5px !important;
    box-shadow: 2px 2px 4px #000000;
    background-color: white;
  }
}
@media screen and (max-width: 955px) {
  .text-title {
    font-size: 35px;
  }
  .my-display-1 {
    font-size: 20px !important;
    color: #6b0000;
    font-family: Roboto, sans-serif !important;
    letter-spacing: normal !important;
    line-height: 40px !important;
    font-weight: 400;
  }
  h1 {
    font-size: 2.5rem;
    font-weight: 500;
    color: #6b0000;
    font-family: Roboto, sans-serif !important;
  }
  .partition {
    border: 0;
    width: 2px !important;
    box-shadow: 2px 2px 4px #000000;
    background-color: white;
  }
}
@media screen and (min-width: 956px) {
  .text-body {
    font-size: 25px;
    font-weight: 500;
  }
}
@media screen and (max-width: 955px) {
  .text-body {
    font-size: 15px;
    font-weight: 500;
  }
}
.content {
  color: white;
}
.toolbar-item-text {
  color: white !important;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.slide-fade-enter-active {
  transition: all 0.5s ease;
}
.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
.v-btn--large {
  padding: 0 20px !important;
}
</style>
