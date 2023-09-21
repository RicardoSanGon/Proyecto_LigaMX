
<script setup>
import { ref } from 'vue';

const Key_EquiposArray=['284','5348','5353','5357','301','5355','303','5356','5351','308','278','5352',
                        '5349','5354','5350','5347','272','275']
let Equipos_LigaMX=ref([])
const key="b65fe0978666b1ec3e7f23f5f5d6b44714437ccbed9146fe0afb2e35abc384dd"

for(let i=0;i<Key_EquiposArray.length;i++)
{
  fetch("https://apiv2.allsportsapi.com/football/?&met=Teams&teamId="+Key_EquiposArray[i]+"&APIkey="+key)
  .then(res=>res.json())
  .then((data)=>{
      Equipos_LigaMX.value.push(data.result)

      
  })
}

console.log(Equipos_LigaMX.value)

</script>

<template>
  <div v-for="(equipo) in Equipos_LigaMX" >
      <div v-for="(inf) in equipo" id="tarjeta_equipos" >
        <v-card
    max-width="100"
  >
    <v-img
      :src="inf.team_logo"
      style="height: 100px;
      width: 300px;"
      cover
    ></v-img>

    <v-card-title>
      {{ inf.team_name }}
    </v-card-title>

  </v-card>
      </div>
  </div>
</template>

<style scoped>
#tarjeta_equipos
{
  display: flex;
  justify-content: center;
}
</style>