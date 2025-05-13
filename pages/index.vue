<template>
    <title>Alexia Moreno Portfolio</title>
    <NavBar :number="1" :isGrey="isGrey" class="fixed w-full top-0 z-30"></NavBar>
    <div class="flex flex-col items-center h-screen absolute top-0 bg-blu w-[99vw] justify-center gap-20"
        @click="isGrey = false" v-if="isGrey">
        <img src="../public/star.svg" alt="" class="w-[27%]">
        <h3 class="uppercase text-grei">
            click to continue
        </h3>
    </div>
    <div class="p-8 mt-20">
        <div class="cont flex flex-col gap-8 p-8 border-black">
            <div class="flex flex-col gap-[400px]">
                <CardPro v-for="(picture, i) in array" :id="i" :isMobile="false"></CardPro>
            </div>
        </div>
    </div>
    <Footer></Footer>

</template>


<script setup>
import { ref, watch } from 'vue';
import { state } from "../public/data.json";

import { gsap } from "gsap";
import { ScrollToPlugin } from "gsap/ScrollToPlugin";
gsap.registerPlugin(ScrollToPlugin);


let array = ref(state.arrayDesign);
let isGrey = ref(true);


</script>

<style lang="sass" scoped>

</style>
