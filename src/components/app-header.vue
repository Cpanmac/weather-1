<template>
  <header class="app-header" id="app-header">
    <div class="city-bottom"
         :class="{'show-temperature': styleCityBottom.opacity === 0}"
    >
      <p>
        <span>{{cityName}}</span>
        <span class="temperature-text">25°</span>
      </p>
    </div>
    <div class="city-top" :style="styleCityBottom">
      <p>{{cityName}}</p>
    </div>
    <i class="btn-menu"
       @click="toggleMenu"
    ></i>
    <transition name="menu">
    <div class="menu-wrap"
         v-show="menuVisible"
         @touchstart.stop.self="toggleMenu"
    >
      <div class="menu">
        <div class="menu-item">
          <a href="###">选项</a>
        </div>
        <div class="menu-item">
          <a href="###">选项</a>
        </div>
        <div class="menu-item">
          <a href="###">选项</a>
        </div>
      </div>
    </div>
    </transition>
  </header>
</template>

<script>
  export default {
    mounted() {
      const scrollDistance = document.querySelector('#app-header').clientHeight / 2;
      let scrollFlag = true;
      window.addEventListener('scroll', () => {
        if (window.scrollY > scrollDistance) {
          this.styleCityBottom.opacity = 0;
          return;
        }
        if (scrollFlag) {
          window.requestAnimationFrame(() => {
            const scrollY = window.scrollY > scrollDistance ? scrollDistance : window.scrollY;
            this.styleCityBottom.opacity = 1 - (scrollY / scrollDistance);
            scrollFlag = true;
          });
        }
        scrollFlag = false;
      });
    },
    data() {
      return {
        menuVisible: false,
        styleCityBottom: {
          opacity: 1,
        },
      };
    },
    props: {
      cityName: {
        type: String,
        default() {
          return '';
        },
      },
    },
    methods: {
      toggleMenu() {
        this.menuVisible = !this.menuVisible;
      },
    },
  };
</script>

<style lang="stylus">
@require '../style/rider'

$height-app-header = .5rem;

.app-header
  position: fixed
  height: $height-app-header
  top: 0
  left: 0
  right: 0
  margin: auto
.btn-menu
  position: absolute
  top: 0
  right: 0
  bottom: 0
  margin: auto
  width: $height-app-header
  height: $height-app-header
  display: block
  background-image: url('../../static/icon-header-menu.svg')
  background-size: .25rem
  background-repeat: no-repeat
  background-position: center
.city-top
.city-bottom
  height: $height-app-header
  line-height: $height-app-header
  padding: 0 .2rem
  position: absolute
  top: 0
  left: 0
  right: 0
  margin: auto
.city-top
  text-align: center
  font-size: .14rem
  background-color: #fff
  transition: opacity .1s
.city-bottom
  font-size: .16rem
.menu-wrap
  position: fixed
  top: 0
  bottom: 0
  left: 0
  right: 0
  margin: auto
.menu
  width: 1rem
  position: absolute
  top: $height-app-header
  right: .2rem
  padding: 0 .1rem
  background-color: #fff
  box-shadow: 0 0 .15rem #ccc

.menu-item
  a
    padding: .1rem 0
    display: block
    color: inherit
    text-decoration: none
  &:not(:last-child)
    border-bottom: solid 1px #ddd
.show-temperature
  .temperature-text
    transform: translate(0,0)
    opacity: 1
.temperature-text
  display: inline-block
  transform: translate(.1rem,0)
  opacity: 0
  transition: transform .4s
.menu-enter-active, .menu-leave-active
  transition: all .35s easing('in-out-sine')
  transform: translateY(0)
.menu-enter, .menu-leave-to
  transform: translateY(-.2rem);
  opacity: 0
</style>
