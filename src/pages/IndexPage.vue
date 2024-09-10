<template>
  <q-page class="">
    <q-tabs class="bg-primary text-white" v-model="tab">
      <q-tab name="attendance" label="Attendance" />
      <q-tab name="homework" label="Homework" />
    </q-tabs>
    <q-tab-panels v-model="tab" swipeable animated>
      <q-tab-panel name="attendance">
        <div class="text-h6">Attendance</div>
        Lorem ipsum dolor sit amet consectetur adipisicing elit.
      </q-tab-panel>

      <q-tab-panel name="homework">
        <div class="text-h6">Homework</div>
        Lorem ipsum dolor sit amet consectetur adipisicing elit.
      </q-tab-panel>
    </q-tab-panels>
  </q-page>
</template>

<script setup>
import { ref } from 'vue';

const tab = ref('attendance');
</script>
