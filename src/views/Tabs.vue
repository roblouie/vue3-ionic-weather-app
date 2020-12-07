<template>
  <ion-page>
    <ion-tabs>
      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="tab1" href="/tabs/tab1">
          <img :src="getWeatherImageUrl(weather?.current?.weather[0].icon, '2x')"/>
          <ion-label>Current {{ formatTemperature(weather?.current?.temp, 'F') }}</ion-label>
        </ion-tab-button>
          
        <ion-tab-button tab="tab2" href="/tabs/tab2">
          <ion-icon :icon="calendarOutline" />
          <ion-label>Forecast</ion-label>
        </ion-tab-button>
      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script lang="ts">
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage } from '@ionic/vue';
import { calendarOutline } from 'ionicons/icons';

import { useWeather } from '@/weather/use-weather';

export default {
  name: 'Tabs',
  components: { IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage },
  setup() {
    const { weather, formatTemperature, getWeatherImageUrl } = useWeather();

    return {
      weather,
      formatTemperature,
      getWeatherImageUrl,
      calendarOutline,
    }
  }
}
</script>

<style scoped>
img {
  height: 26px;
  width: 26px;
  margin-bottom: 0px;
  margin-top: 3px;
  background-color: skyblue;
  border-radius: 100%;
}
</style>