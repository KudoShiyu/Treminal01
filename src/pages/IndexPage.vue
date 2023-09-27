<template>
  <div class="fullscreen bg-grey-3 q-pa-md column">
    <div class="q-gutter-md col row">
      <q-btn
        flat
        class="bg-grey-2 col"
        @click="pub(i)"
        v-for="i in indices"
        :key="i"
        :ripple="{ color: 'white' }"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
const indices = [0, 1, 2, 3, 4, 5, 6, 7];

import * as mqtt from 'mqtt/dist/mqtt.min';
// import mqtt from 'mqtt';
console.log('before');

const client = mqtt.connect('wss://test.mosquitto.org:8081');

console.log('after');

const pub = (index: number) => {
  console.log(index);
  client.publish('esp8266/text', Buffer.from(new Uint8Array([index])));
};
</script>
