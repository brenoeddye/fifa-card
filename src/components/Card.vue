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
                {{ club }}
            </div>
        </div>
        <div class="card__image">
            {{ playerImg }}
        </div>
        <div class="card__name">
            {{ playerName }}
        </div>
        <div class="card__stats">
            <ul>
                <li>{{ playerPace }} PAC</li>
                <li>{{ playerShot }} SHO</li>
                <li>{{ playerPass }} PAS</li>
            </ul>
            <ul>
                <li>{{ playerDribling }} DRI</li>
                <li>{{ playerDefense }} DEF</li>
                <li>{{ playerPhysic }} PHY</li>
            </ul>
        </div>
        <div class="card__buff">
            {{ buff }}
        </div>
    </div>
</template>