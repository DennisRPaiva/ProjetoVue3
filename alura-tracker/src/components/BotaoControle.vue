<template>
    <button class="button" @click="handleClick" :disabled="disabled">
        <span class="icon">
        <i :class="iconClass"></i>
        </span>
        <span>{{ label }}</span>
    </button>
</template>

<script>
export default {
    name:"Botao-component",
    props: {
        label: {
        type: String,
        required: true,
        },
        iconClass: {
        type: String,
        required: true,
        },
        disabled: {
        type: Boolean,
        default: false,
        },
    },
    emits: ['iniciar', 'finalizar'],
    methods: {
        handleClick() {
            if (this.label === 'Play') {
                this.$emit('iniciar');
            } else if (this.label === 'Stop') {
                this.$emit('finalizar');
            }
        },
    },
};
</script>

<style scoped>
.button {
  /* Adicione seu estilo aqui */
}
</style>