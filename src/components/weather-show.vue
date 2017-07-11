<template>
  <div class="weather-info">
    <p class="weather-info-text">{{weather}}</p>
    <p class="weather-info-tmp">{{tmp}}</p>
    <p class="weather-info-lastTmp">{{lastTmp}}°</p>
    <p class="weather-info-aqi"><i class="icon-aqi"></i> {{aqi}}</p>
  </div>
</template>

<style lang="stylus">
@require '../assets/style/variable.styl'

.weather-info
  padding: $height-app-header + .7rem 0 1rem
  height: 10rem
  text-align: center
  color: #0b2b60
.weather-info-text
  font-size: .2rem
  margin: 0 0 .35rem
.weather-info-tmp
  position: relative
  font-size: 1.1rem
  &:after
    content: '°'
    position: absolute
.weather-info-lastTmp
  font-size: .16rem
  margin: .15rem 0
.weather-info-aqi
  display: inline-block
  padding: .05rem .15rem
  font-size: .18rem
  border: solid 2px $color-base
  border-radius: .2rem
.icon-aqi
  display: inline-block
  width: .18rem
  height: .18rem
  background-image: url('../assets/img/icon/icon-aqi.svg')
  background-repeat: no-repeat
  background-size: contain
  background-position: center
  vertical-align: middle
</style>

<script>
export default {
  data() {
    return {
    };
  },
  props: {
    // 天气
    weather: {
      type: String,
    },
    // 体感温度
    tmp: {
      type: Number,
    },
    lastTmp: {
      type: String,
    },
    // 空气质量指数
    aqi: {
      type: String,
    },
  },
};
</script>
