<script setup>
 import { ref } from 'vue';
 import LeafletMap from '../components/LeafletMap.vue';
  
 let coords = ref([59.42691, 24.74344]); // Initial map center
 let zoom = ref(19);
 let homeCoords = [59.439809, 24.756078];
 let homePolygon = [
   [59.440028, 24.755953], // Top-left corner
   [59.439829, 24.756491], // Top-right corner
   [59.439649, 24.756363], // Bottom-right corner
   [59.439761, 24.755739], // Bottom-left corner
   [59.440028, 24.755953]  // Back to first point to close polygon
 ];
</script>
 
     <template>
     <button class="button is-primary" @click="coords=homeCoords">Go to my home</button>
     <input type="range" min="1" max="19" step="1" v-model="zoom">
     <LeafletMap 
         :center="coords" 
         :zoom="zoom"
         :marker="homeCoords"
         :polygon="homePolygon"
     ></LeafletMap>
     </template>