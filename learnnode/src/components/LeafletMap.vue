<script setup>
 import L from 'leaflet';
 import 'leaflet/dist/leaflet.css';
 import { onMounted, useId, watch } from 'vue';
 
 let { center, zoom } = defineProps(['center', 'zoom']);
 
 let id = 'map-' + useId();
 let map;
 onMounted(() => {
     console.log(document.getElementById(id));
 
     map = L.map(id).setView(center, zoom);
     L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
         maxZoom: 19,
         attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
     }).addTo(map);
 });
 
 watch(() => center, (newCenter, oldCenter) => {
     console.log(newCenter, oldCenter);
     map.panTo(newCenter);
 });
 watch(() => zoom, newZoom => {
     map.setZoom(newZoom);
 });
 </script>
 <template>
      <div :id="id"></div>
 </template>
 
 <style scoped>
 div { 
     height: 40vh;
 }
 </style>