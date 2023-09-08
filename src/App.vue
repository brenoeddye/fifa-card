<script lang="ts">
import Card from '@/components/Card.vue'
import Steps from '@/components/Steps.vue'
import { defineComponent } from '@vue/runtime-core'

export default defineComponent({
  components: { Card, Steps },
  data() {
    return {
      playerOver: '99',
      playerName: 'Seu nome',
      playerPos: 'ATA',
      options:[
        { opt: ['Ataque', 'ATA', 'PE', 'PD', 'MAE', 'MAD'] },
        { opt: ['Meio-Campo', 'MEI','MC','ME','MD','VOL'] },
        { opt: ['Defesa', 'ADD', 'ADE', 'ZAG', 'LE', 'LD', 'GOL'] }
      ],
      userStep: 0
    }
  }
})
</script>

<template>
  <div class="app">
    <Card 
      type="gold"
      :overall="playerOver"
      :position="playerPos"
      nation="france"
      league="ligue1"
      club="psg"
      playerImg="guest"
      :playerName="playerName"
      playerPace="97"
      playerShot="89"
      playerPass="80"
      playerDribling="92"
      playerDefense="36"
      playerPhysic="76"
      buff="hunter"
    />

    <Steps />
  </div>
</template>