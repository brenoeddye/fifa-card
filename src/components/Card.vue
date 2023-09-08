<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    props: {
        type: String,
        overall: String,
        position: String,
        nation: String,
        league: String,
        club: String,
        playerImg: String,
        playerName: String,
        playerPace: String,
        playerShot: String,
        playerPass: String,
        playerDribling: String,
        playerDefense: String,
        playerPhysic: String,
        buff: String
    }
})
</script>


<template>
    <div :class="'card ' + type">
        <div class="card__top">
            <div class="card__top--ovrl">
                <input type="text" :value="overall">
                <p>{{ position }}</p>
            </div>
            <div class="card__top--nation">
                <img :src="'./images/nations/'+ nation + '.png'" alt="Player Nation">
            </div>
            <div class="card__top--club">
                <img :src="'./images/leagues/' + league + '/' + club + '.png'" alt="">
                
            </div>
        </div>
        <div class="card__image">
            <img :src="'./images/guest.png'" alt="">
        </div>
        <div class="card__name">
            <input type="text" :value="playerName">
        </div>
        <div class="card__stats">
            <ul>
                <li><b><input type="text" :value="playerPace"></b> PAC</li>
                <li><b><input type="text" :value="playerShot"></b> SHO</li>
                <li><b><input type="text" :value="playerPass"></b> PAS</li>
            </ul>
            <ul>
                <li><b><input type="text" :value="playerDribling"></b> DRI</li>
                <li><b><input type="text" :value="playerDefense"></b> DEF</li>
                <li><b><input type="text" :value="playerPhysic"></b> PHY</li>
            </ul>
        </div>
        <i :class="'card__buff ' + buff"></i>
    </div>
</template>