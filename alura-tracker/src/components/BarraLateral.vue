<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="">
        </h1>
        <button class="button" @click="alterarTema">
           {{ textoBotao }}
        </button>
    </header>
    
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'BarraLateral',
    emits: ['aoTemaAlterado'],
    data () {
        return {
            modoClaroAtivo: false
        }
    },
    computed: {
        textoBotao() {
            if(this.modoClaroAtivo) {
                return 'Desativar modo claro'
            }
            return 'Ativar modo claro'
        }
    },
    methods: {
        alterarTema() {
            this.modoClaroAtivo = !this.modoClaroAtivo
            this.$emit('aoTemaAlterado', this.modoClaroAtivo)
        }
    }
})
</script>

<style scoped>
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center
}
@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>