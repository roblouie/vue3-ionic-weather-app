<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Weather</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-grid>
        <ion-row>

          <ion-col size="12" size-lg="5">
            <current-weather></current-weather>
          </ion-col>

          <ion-col size="12" size-lg="4">
            <forecast></forecast>
          </ion-col>

        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import commonIonicComponents from '@/shared/common-ionic-components';
import { defineComponent } from 'vue'

import CurrentWeather from './current-weather.vue';
import Forecast from './forecast.vue';

export default defineComponent({
  components: {
    CurrentWeather,
    Forecast,
    ...commonIonicComponents,
  },
  setup () {
    

    return {}
  }
})
</script>

<style scoped>

</style>