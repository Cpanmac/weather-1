<template>
  <div>
    <app-header :city-name="cityName"></app-header>
    <weather-show
      :weather="weather"
      :tmp="tmp"
      :last-tmp="lastTmp"
      :aqi="aqi"
    ></weather-show>
  </div>

</template>
<script>
  import AppHeader from '@/components/app-header';
  import WeatherShow from '@/components/weather-show';

  export default {

    data() {
      return {
        cityName: '城市',
        weather: '阴',
        tmp: 32,
        lastTmp: '比昨天高5°C',
        aqi: '123 轻度',
      };
    },
    methods: {
    },
    components: {
      AppHeader,
      WeatherShow,
    },
  };
</script>
