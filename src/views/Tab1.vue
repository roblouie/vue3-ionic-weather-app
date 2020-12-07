<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Current Weather</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Current Weather</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-grid>
        <ion-row class="ion-justify-content-center">
          <ion-col size="auto" class="min-width">
            <current-weather></current-weather>
          </ion-col>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import ExploreContainer from '@/components/ExploreContainer.vue';
import CurrentWeather from '@/weather/current-weather.vue';
import commonIonicComponents from '@/shared/common-ionic-components';

export default  {
  name: 'Tab1',
  components: { 
    CurrentWeather,
    ...commonIonicComponents 
  }
}
</script>

<style scoped>
.min-width {
  min-width: 350px;
}
</style>
