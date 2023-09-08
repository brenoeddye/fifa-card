<script lang="ts">
import type { CardDesign } from '@/core/types/ICardDesign';
import cardContent from '@/core/data/CardDesign';
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
    },
    data() {
        return {
            actualCard: null as CardDesign | null,
            nextCard: '',
            prevCard: ''
        };
    },
    watch: {
        type(newType) {
            this.actualCard = this.findCardByType(newType);
        },
        actualCard(newActualCard) {
            this.updateNextAndPrevCards(newActualCard);
        }
    },
    computed: {
        findCardByType(): (type: string) => CardDesign | null {
            return (type: string) => {
                return cardContent.find(card => card.name === type) || null;
            };
        }
    },
    created() {
        this.actualCard = this.findCardByType(this.type as string);
    },
    methods: {
        updateNextAndPrevCards(newActualCard: CardDesign | null) {
            if (newActualCard) {
                const index = cardContent.findIndex(card => card.name === newActualCard.name);
                const lastIndex = cardContent.length - 1;

                const nextIndex = (index + 1) % cardContent.length;
                const prevIndex = (index - 1 + cardContent.length) % cardContent.length;

                this.nextCard = cardContent[nextIndex].name;
                this.prevCard = cardContent[prevIndex].name;
            } else {
                this.nextCard = '';
                this.prevCard = '';
            }
        },
        showNextCard() {
            if (this.nextCard) {
                this.actualCard = this.findCardByType(this.nextCard);
            }
        },
        showPrevCard() {
            if (this.prevCard) {
                this.actualCard = this.findCardByType(this.prevCard);
            }
        }
    }
})
</script>

<template>
    <div class="card__prev" :style="'background-image: url(./images/cards/' + prevCard + '.png'"></div>
    <div class="card" :style="'background-image: url(./images/cards/' + (actualCard ? actualCard.name : '') + '.png'">
        <div class="card__top">
            <div class="card__top--ovrl">
                <input type="text" :value="overall" :style="'color:' + (actualCard ? actualCard.color1 : '')">
                <p :style="'color:' + (actualCard ? actualCard.color1 : '')">{{ position }}</p>
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
            <input type="text" :value="playerName" :style="'color:' + (actualCard ? actualCard.color1 : '') + ';border-bottom: 1px solid' + (actualCard ? actualCard.color2 : '') +';'">
        </div>
        <div class="card__stats">
            <ul :style="'color:' + (actualCard ? actualCard.color1 : '')">
                <li><b><input type="text" :value="playerPace" :style="'color:' + (actualCard ? actualCard.color1 : '')"></b> PAC</li>
                <li><b><input type="text" :value="playerShot" :style="'color:' + (actualCard ? actualCard.color1 : '')"></b> SHO</li>
                <li><b><input type="text" :value="playerPass" :style="'color:' + (actualCard ? actualCard.color1 : '')"></b> PAS</li>
            </ul>
            <ul :style="'color:' + (actualCard ? actualCard.color1 : '')">
                <li><b><input type="text" :value="playerDribling" :style="'color:' + (actualCard ? actualCard.color1 : '')"></b> DRI</li>
                <li><b><input type="text" :value="playerDefense" :style="'color:' + (actualCard ? actualCard.color1 : '')"></b> DEF</li>
                <li><b><input type="text" :value="playerPhysic" :style="'color:' + (actualCard ? actualCard.color1 : '')"></b> PHY</li>
            </ul>
        </div>
        <i :class="'card__buff ' + buff" :style="'color:' + (actualCard ? actualCard.color1 : '')"></i>
    </div>
    <div class="card__next" :style="'background-image: url(./images/cards/' + nextCard + '.png'"></div>
    <div class="card__controls">
        <button class="card__controls--button back" @click="showPrevCard">Anterior</button>
        <button class="card__controls--button next" @click="showNextCard">Próximo</button>
    </div>
</template>