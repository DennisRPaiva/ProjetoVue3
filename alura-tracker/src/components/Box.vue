<template>
    <div class="box has-text-weight-bold">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'Box-component'
})

</script>

<style scoped>
.box {
    background: #A9A9A9;
    color: #1E1A33;
}
</style>