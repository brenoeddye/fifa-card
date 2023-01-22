<script lang="ts">
import Card from '@/components/Card.vue'
import Steps from '@/components/Steps.vue'
import { defineComponent } from '@vue/runtime-core'

export default defineComponent({
  components: { Card, Steps },
  data() {
    return {
      playerOver: '99',
      playerName: 'Seu nome'
    }
  }
})
</script>

<template>
  <div class="app">
    <div class="menu">
        <h1>Criação de Card</h1>
        <div class="menu__content">
          <section class="menu__content--section">
            <h2>Overal e Posição</h2>
            <input type="number" v-model="playerOver" max="99" min="0" maxlength="2"/>
            <input type="text" v-model="playerName" maxlength="20"/>
          </section>
          <section class="menu__content--section">
            <h2>País e clube</h2>
          </section>
        </div>
    </div>

    <Card 
      type="gold"
      :overall="playerOver"
      position="ST"
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