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
    <div class="menu">

        <h2>Criação de Card</h2>

        <Transition name="fade">
          <div v-if="userStep == 0" class="menu__content">
            <section class="menu__content--section">
              <input type="text" v-model="playerName" maxlength="20"/>
              <input type="number" v-model="playerOver" max="99" min="0" maxlength="2"/>
              <select v-model="playerPos">
                <optgroup v-for="(option, index) in options" :key="option.opt" :label="option.opt[0]">
                  <option> {{ option.opt[index] }}</option>
                </optgroup>
              </select>
            </section>

            <section class="menu__content--btn-group">
              <button @click="userStep++" class="primary">Avançar</button>
            </section>
          </div>
        </Transition>

        <Transition name="fade">
          <div v-if="userStep == 1" class="menu__content">

            <section class="menu__content--btn-group">
              <button @click="userStep--" class="secondary">Voltar</button>
              <button @click="userStep++" class="primary">Avançar</button>
            </section>
          </div>
        </Transition>
    </div>

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