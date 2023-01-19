<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    setup() {
        
    },
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
                <span>{{ overall }}</span>
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
            {{ playerName }}
        </div>
        <div class="card__stats">
            <ul>
                <li><b>{{ playerPace }}</b> PAC</li>
                <li><b>{{ playerShot }}</b> SHO</li>
                <li><b>{{ playerPass }}</b> PAS</li>
            </ul>
            <ul>
                <li><b>{{ playerDribling }}</b> DRI</li>
                <li><b>{{ playerDefense }}</b> DEF</li>
                <li><b>{{ playerPhysic }}</b> PHY</li>
            </ul>
        </div>
        <i :class="'card__buff ' + buff"></i>
    </div>
</template>