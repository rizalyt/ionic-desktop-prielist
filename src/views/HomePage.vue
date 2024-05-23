<template>
  <ion-content>
    <ion-grid>
      <ion-row>
        <ion-col size="12" class="ion-text-center" style="text-align: center;">
          <ion-button @click="getData" style="text-transform: capitalize;">
            Get Data
          </ion-button>
        </ion-col>
      </ion-row>
      <ion-row v-if="items.length > 0" style="border: 4px solid black; padding: 30px;">
        <ion-col size="4" style="text-align: center;">Name</ion-col>
        <ion-col size="4" style="text-align: center;">Symbol</ion-col>
        <ion-col size="4" style="text-align: center;">Harga USD</ion-col>
      </ion-row>

      <ion-row v-for="item in items" :key="id">
        <ion-col size="4" style="text-align: center; padding: 15px;">{{ item.name }}</ion-col>
        <ion-col size="4" style="text-align: center; padding: 15px;">{{ item.symbol }}</ion-col>
        <ion-col size="4" style="text-align: center; padding: 15px;">{{ item.price_usd }}</ion-col>
      </ion-row>
    </ion-grid>
  </ion-content>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      items: []
    }
  },
  methods: {
    getData() {
      axios.get('https://api.coinlore.net/api/tickers/')
        .then(response => {
          this.items = response.data.data
        }).catch(error => {
          console.log(error);
        });
    }
  },
}
</script>








<!-- <template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <strong>Ready to create an app?</strong>
        <p>Start with Ionic <a target="_blank" rel="noopener noreferrer" href="https://ionicframework.com/docs/components">UI Components</a></p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</> -->
