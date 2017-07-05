<template>
  <div>
    <app-header :city-name="cityName"></app-header>
    <weather-show></weather-show>
  </div>

</template>
<script>
  import AppHeader from '@/components/app-header';
  import WeatherShow from '@/components/weather-show';

  export default {

    data() {
      return {
        cityName: '城市',
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
