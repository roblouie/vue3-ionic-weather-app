<template>
  <ion-list>
    <ion-list-header>
      Forecast
    </ion-list-header>

    <ion-item v-for="daily in weather?.daily" :key="daily.dt">
      <ion-avatar slot="start">
        <div class="weather-background">
          <img :src="getWeatherImageUrl(daily.weather[0].icon, '2x')">
        </div>
      </ion-avatar>
      <ion-label>
        <h1>{{ formatTemperature(daily.temp.day, 'F') }}</h1>
        <h2>{{ daily.weather[0].description }}</h2>
        <p>{{ new Date(daily.dt * 1000).toLocaleDateString(undefined, { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }) }}</p>
      </ion-label>
    </ion-item>
  </ion-list>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue'
import { IonList, IonListHeader, IonItem, IonAvatar, IonLabel } from '@ionic/vue';
import commonIonicComponents from '@/shared/common-ionic-components';
import { useWeather } from './use-weather'

export default defineComponent({
  components: {
    IonList,
    IonListHeader,
    IonItem,
    IonAvatar,
    IonLabel,
    ...commonIonicComponents
  },
  setup () {
    const { weather, fetchWeather, getWeatherImageUrl, formatTemperature } = useWeather();
    onMounted(fetchWeather);

    return {
      weather,
      getWeatherImageUrl,
      formatTemperature
    }
  }
})
</script>

<style scoped>
.weather-background {
  background-color: skyblue;
  border-radius: 100%;
  border: 2px solid white;
}
</style>