<template>
    <div :class="['flex', 'justify-between', 'items-center', 'p-5', isGrey ? 'bg-transparent' : 'bg-white']">
        <nuxt-link to="/" class="logo">
            <img src="../public/grey_logo.svg" alt="" class="w-24" v-if="isGrey">
            <img src="../public/logo.svg" alt="" class="w-24" v-else>
        </nuxt-link>
        <nav :class="['navigation', 'flex', 'list-none', 'uppercase', 'gap-7', 'p-3', isGrey ? 'text-grei' : 'text-blu']">
            <li :class="['bodylarge', { bold: number === 1 }]">
                <nuxt-link to="/">Proyectos</nuxt-link>
            </li>
            <li :class="['bodylarge', { bold: number === 2 }]">
                <nuxt-link to="/sketch">Sketchbook</nuxt-link>
            </li>
            <li :class="['bodylarge', { bold: number === 3 }]">
                <nuxt-link to="/contacto">Contacto</nuxt-link>
            </li>
        </nav>
    </div>
</template>


<script setup>
const props = defineProps({
    number: Number,
    isMobile: Boolean,
    isGrey: Boolean
})
</script>


<style lang="sass" scoped>

</style>