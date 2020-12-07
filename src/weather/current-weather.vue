<template>
    <ion-card v-if="weather?.current">
      <div class="weather-background">
        <img :src="getWeatherImageUrl(weather.current?.weather[0].icon, '4x')"/>
      </div>
      <ion-card-header>
        <ion-card-subtitle>{{ weather.current.weather[0].description }}</ion-card-subtitle>
        <ion-card-title>{{ formatTemperature(weather.current.temp, 'F') }}</ion-card-title>
      </ion-card-header>

      <ion-card-content>
        <ion-grid>

          <ion-row>
            <ion-col>
              Feels like {{ parseInt(weather.current.feels_like) }} &deg; F
            </ion-col>

            <ion-col>
              Wind Speed {{ parseInt(weather.current.wind_speed) }} mph
            </ion-col>
          </ion-row>

          <ion-row>
            <ion-col>
              Sunrise {{ new Date(weather.current.sunrise * 1000).toLocaleTimeString([], { timeStyle: 'short' }) }}
            </ion-col>

              <ion-col>
              Sunset {{ new Date(weather.current.sunset * 1000).toLocaleTimeString([], { timeStyle: 'short' }) }}
            </ion-col>
          </ion-row>
        </ion-grid>
      </ion-card-content>

    </ion-card>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import commonIonicComponents from '@/shared/common-ionic-components';
import { useWeather } from './use-weather';

export default defineComponent({
  components: {
    ...commonIonicComponents,
  },
  setup () {
    const { weather, fetchWeather, getWeatherImageUrl, formatTemperature } = useWeather();
    if (!weather?.value?.current) {
      fetchWeather();
    }

    return {
      weather,
      getWeatherImageUrl,
      formatTemperature
    }
  }
})
</script>

<style scoped>
ion-card {
  max-width: 350px;
}

ion-card img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.weather-background {
  background-color: skyblue;
}
</style>