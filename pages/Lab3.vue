<template>
  <div style="height:100vh; width:100vw">
    <LMap 
      :zoom="11" 
      :center="petropavl" 
      :use-global-leaflet="false"
      style="height:100%; width:100%;"
    >
      <LTileLayer
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
        attribution="&copy; OpenStreetMap contributors"
      />
      
      <!-- Маркер города -->
      <LMarker :lat-lng="petropavl" :draggable="false">
        <LTooltip permanent direction="top">Петропавловск (СКО)</LTooltip>
        <LPopup>Петропавловск, Северо-Казахстанская область</LPopup>
      </LMarker>
      
      <!-- Зафиксированные озёра -->
      <LMarker
        v-for="(lake, i) in lakes"
        :key="i"
        :lat-lng="[lake.lat, lake.lng]"
        :draggable="false"
      >
        <LTooltip permanent direction="top">{{ lake.name }}</LTooltip>
        <LPopup>
          <strong>{{ lake.name }}</strong><br />
          Уровень воды: {{ lake.level }}
        </LPopup>
      </LMarker>
    </LMap>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { LMap, LTileLayer, LMarker, LTooltip, LPopup } from '@vue-leaflet/vue-leaflet'
import 'leaflet/dist/leaflet.css'

type LatLngTuple = [number, number]

interface Lake {
  name: string
  lat: number
  lng: number
  level: number
}

// Центр карты - Петропавловск
const petropavl = ref<LatLngTuple>([54.88, 69.16]) //координаты Петропавловска

// Список озёр
const lakes = ref<Lake[]>([
  { name:'Озеро Пёстрое', lat: 54.836674, lng: 69.109874, level: -0.14},
  { name:'Озеро Белое', lat: 55.035607, lng: 70.194716, level: -0.19},
  { name:'Озеро Горькое', lat: 54.948484, lng: 68.950702, level: -0.32},
  { name:'Озеро Поганка', lat: 54.921344, lng: 69.052130, level: -0.11},
  { name:'Озеро Дикое', lat: 54.840156, lng: 69.131957, level: -0.24},
  { name:'Озеро Полковниково', lat: 55.172774, lng: 69.249948, level: -0.15},
  { name:'Озеро Никульское', lat: 55.263029, lng: 69.357153, level: -0.27},
])
</script>
