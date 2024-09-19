<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <Cronometro :tempoEmSegundos ="tempoEmSegundos"/>
        <BotaoControle
            label="Play"
            iconClass="fas fa-play"
            :disabled="cronometroRodando"
            @iniciar="iniciar"
        />
        <BotaoControle
            label="Stop"
            iconClass="fas fa-stop"
            :disabled="!cronometroRodando"
            @finalizar="finalizar"
        />
    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import Cronometro from './Cronometro.vue';
import BotaoControle from './BotaoControle.vue';

export default defineComponent({
    name:"Temporizador-component",
    emits:['aoTemporizadorFinalizado'],
    components: {
        Cronometro,
        BotaoControle
    },
    data () {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods: {
        iniciar () {
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000)
            
        },
        finalizar () {
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})

</script>