<script setup>
import { ref } from 'vue';

const Key_EquiposArray=['284','5348','5353','5357','301','5255','303','5356','5351','300','278','5352',
                        '5349','5354','5350','5347','272','275']
let Equipos_LigaMX=ref({})
const key="b65fe0978666b1ec3e7f23f5f5d6b44714437ccbed9146fe0afb2e35abc384dd"

for(i=0;i<Key_EquiposArray.length;i++)
{
  fetch("https://apiv2.allsportsapi.com/football/?&met=Teams&teamId="+Key_EquiposArray[i]+"&APIkey="+key)
  .then(res=>res.json())
  .then((data)=>{
      Equipos_LigaMX.value=data.result.team_logo
      console.log(Equipos_LigaMX.value)
  })
}


</script>

<template>
  <div v-for="(item, Equipos_LigaMX) in items">
      <img :src="item">
  </div>
</template>
  
