<script lang="ts">
import Card from '@/components/Card.vue'
import { defineComponent } from '@vue/runtime-core'

export default defineComponent({
  components: { Card },
  data() {
    return {

    }
  }
})
</script>

<template>
  <div class="app">
    <Card 
      type="wc"
      overall="91"
      position="ST"
      nation="france"
      club="PSG"
      playerImg="some"
      playerName="Mbappé"
      playerPace="97"
      playerShot="89"
      playerPass="80"
      playerDribling="92"
      playerDefense="36"
      playerPhysic="76"
      buff="Hunter"
    />
  </div>
</template>