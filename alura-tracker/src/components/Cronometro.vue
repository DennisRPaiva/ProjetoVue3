<template>
    <section>
        <strong class="display" :style="{ color: color }">
            {{ tempoDecorrido }}
        </strong>
    </section>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';

export default defineComponent({
    name: 'Cronometro-component',
    props: {
        tempoEmSegundos: {
            type: Number,
            default: 0,
        },
        color: {
            type: String as PropType<string>,
            required: false,
            default: '#FFFFF', // cor padrão
        },
    },
    computed: {
        tempoDecorrido(): string {
            return new Date(this.tempoEmSegundos * 1000).toISOString().substring(11, 19);
        },
    },
});
</script>

<style scoped>
.display {
    color: var(--texto-primario)
}
</style>
