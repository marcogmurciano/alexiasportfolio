<template>
    <div class="flex py-4 px-10 border rounded-full text-blu border-blu bg-white bodylarge cursor-pointer">
        <slot/>
    </div>
</template>

<script setup>
const props = defineProps({
    state: Number
})
</script>


<style lang="sass" scoped>
.flex:hover
    @apply text-black border-black
.flex:active
    @apply bg-blu text-white
</style>