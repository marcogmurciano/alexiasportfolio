<template>
    <title>proyecto</title>
    <NavBar :number="1" class="fixed w-full top-0"></NavBar>

    <div class="flex justify-between m-12 pt-12 gap-12">
        <div class="flex flex-col justify-between">
            <div class="flex flex-col gap-4">
                <h3>
                    {{ array[param].title }}
                </h3>
                <p class="bodysmall">
                    {{ array[param].description }}
                </p>
            </div>
            <div class="flex justify-between">
                <div class="date">
                    {{ array[param].date }}
                </div>
                <a :href="array[param].link" v-if="array[param].link != ''" class="flex items-center">
                    <Button>View Post</Button>
                </a>
            </div>
        </div>

        <div class="IMAGES flex flex-col gap-4 w-[777px]">
            <div class="cont h-[533px] flex justify-center">
                <img :src="array[param].pictures[indices[0]]" alt="Principal" :class="imageClass"
                    @load="handleImageLoad" />
            </div>
            <div class="flex gap-4">
                <div v-for="(idx, slot) in [1, 2, 3]" :key="idx" class="cont w-64 h-44 overflow-hidden">
                    <img :src="array[param].pictures[indices[idx]]" :alt="`Miniatura ${idx}`" class="cursor-pointer"
                        @click="swapIndices(0, idx)" />
                </div>
            </div>
        </div>
    </div>
    <Footer></Footer>
</template>


<script setup>

import { ref, watch } from 'vue';
import { useRoute } from 'vue-router';
import { state } from "../public/data.json";

let array = ref(state.arrayDesign);

const route = useRoute();
const param = ref(Number(route.query.ind));


const imageWidth = ref(0);
const imageHeight = ref(0);
const imageClass = ref("");

// Lógica para manejar el evento de carga de la imagen
const handleImageLoad = (event) => {
    // Accede a las dimensiones reales de la imagen
    const img = event.target;
    imageWidth.value = img.naturalWidth;
    imageHeight.value = img.naturalHeight;

    // Aplica la lógica para determinar la clase en función de la relación de aspecto
    if (imageWidth.value > imageHeight.value) {
        imageClass.value = "h-fit";
    } else {
        imageClass.value = "h-full";
    }
};


const indices = reactive([0, 1, 2, 3])

const swapIndices = (posA, posB) => {
    const tmp = indices[posA]
    indices[posA] = indices[posB]
    indices[posB] = tmp
}



watch(() => route.query.ind, (newInd) => {
    param.value = Number(newInd);
});



</script>


<style lang="sass" scoped>

</style>